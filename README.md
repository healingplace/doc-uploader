# UploaderDoc - PDF Processing Web Application

A modern Blazor WebAssembly Progressive Web App (PWA) for document management and PDF processing, built with .NET 9.0 and Microsoft FluentUI components.

## 🌟 Features

### 📁 Document Management
- **File Upload**: Secure document upload with Azure Blob Storage integration
- **Multi-format Support**: Upload various image formats and documents
- **Progress Tracking**: Real-time upload progress with visual indicators
- **File Validation**: Automatic file type and size validation

### 📄 PDF Processing
- **PDF Merge**: Combine multiple PDF files into a single document
  - Support for up to 10 PDF files (50MB each)
  - Drag-and-drop file selection
  - Real-time file management (add/remove files)
  - Order preservation during merge
- **File to PDF Conversion**: Convert image files to PDF format
  - Supported formats: JPEG, PNG, BMP, TIFF, WEBP
  - Batch conversion (up to 20 files)
  - A4 page size with automatic image scaling
  - Individual PDF downloads

### 🔐 Authentication & Security
- **Azure AD B2C Integration**: Secure user authentication
- **Role-based Access**: Protected routes for authenticated users
- **Token Management**: Automatic token refresh and validation
- **Secure API Access**: Bearer token authentication for backend services

### 🎨 Modern UI/UX
- **FluentUI Design**: Microsoft's modern design system
- **Responsive Layout**: Works on desktop, tablet, and mobile
- **Dark/Light Theme**: Automatic theme support
- **Progressive Web App**: Installable web application
- **Accessibility**: WCAG compliant interface

## 🛠️ Technology Stack

### Frontend
- **Framework**: Blazor WebAssembly (.NET 9.0)
- **UI Library**: Microsoft FluentUI Components 4.13.1
- **Icons**: FluentUI Icons 4.13.1
- **Authentication**: Microsoft Authentication Library (MSAL) 9.0.0
- **PWA**: Service Worker integration

### Backend Integration
- **Cloud Storage**: Azure Blob Storage 12.26.0
- **PDF Processing**: iText7 7.2.5 (WebAssembly compatible)
- **HTTP Client**: Built-in .NET HTTP client with authentication

### Development Tools
- **IDE Support**: Visual Studio, VS Code
- **Build System**: .NET SDK with MSBuild
- **Package Management**: NuGet
- **Version Control**: Git with GitHub Actions

## 🚀 Getting Started

### Prerequisites
- [.NET 9.0 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- [Visual Studio 2022](https://visualstudio.microsoft.com/) or [VS Code](https://code.visualstudio.com/)
- [Node.js](https://nodejs.org/) (for Azure Static Web Apps CLI)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/manishmawat/doc-uploader.git
   cd doc-uploader
   ```

2. **Restore dependencies**
   ```bash
   dotnet restore
   ```

3. **Configure Azure AD B2C** (Optional for PDF features)
   Update `wwwroot/appsettings.json`:
   ```json
   {
     "AzureAd": {
       "ClientId": "your-client-id",
       "Authority": "https://your-tenant.ciamlogin.com/",
       "Scopes": ["openid", "profile", "offline_access"]
     }
   }
   ```

4. **Run the application**
   ```bash
   dotnet run
   ```

5. **Access the app**
   Open your browser to `https://localhost:7229` or `http://localhost:5168`

### Development Commands

```bash
# Build the project
dotnet build

# Run in development mode
dotnet run

# Publish for production
dotnet publish -c Release

# Clean build artifacts
dotnet clean
```

## 📱 Application Pages

### 🏠 Home (`/`)
- Welcome page with authentication status
- Quick navigation to main features
- User profile display for authenticated users

### 📁 Document Upload (`/docimport`)
- **Protected Route** (requires authentication)
- Multi-file drag-and-drop upload
- Azure Blob Storage integration
- Real-time progress tracking

### 🔗 PDF Merge (`/pdfmerge`)
- **Public Route** (no authentication required)
- Select and combine multiple PDF files
- File preview and management
- Download merged document

### 🔄 File Converter (`/fileconvert`)
- **Public Route** (no authentication required)
- Convert images to PDF format
- Batch processing support
- Individual file downloads

### 🔐 Authentication (`/authentication/*`)
- Azure AD B2C login/logout flows
- Token management
- Redirect handling

## 🏗️ Architecture

### Project Structure
```
UploaderDoc/
├── Components/          # Reusable UI components
├── Layout/             # Application layout components
├── Pages/              # Razor pages/components
├── Services/           # Business logic and API services
├── Authentication/     # Auth configuration
├── wwwroot/           # Static files and configuration
└── Properties/        # Launch settings
```

### Key Services

#### `IPdfMergeService`
- Combines multiple PDF streams into a single document
- Uses iText7 for PDF manipulation
- Optimized for WebAssembly environment

#### `IFileConverterService`
- Converts image files to PDF format
- Supports multiple image formats
- A4 page sizing with automatic scaling

#### `IDocumentUploadService`
- Handles file uploads to Azure Blob Storage
- SAS token management
- Progress tracking

## 🔧 Configuration

### Application Settings
The app supports multiple environment configurations:

- `appsettings.json` - Base configuration
- `appsettings.Development.json` - Development overrides
- `appsettings.Production.json` - Production overrides

### Azure AD B2C Setup
1. Create an Azure AD B2C tenant
2. Register a Single Page Application (SPA)
3. Configure redirect URIs
4. Update `appsettings.json` with tenant details

### Azure Blob Storage (Optional)
1. Create an Azure Storage Account
2. Set up a container for document storage
3. Configure SAS token generation API
4. Update blob storage settings

## 🚀 Deployment

### Azure Static Web Apps
The application is configured for Azure Static Web Apps deployment:

1. **GitHub Actions**: Automated CI/CD pipeline
2. **Build Configuration**: .NET 9.0 build process
3. **Static Files**: Optimized for CDN delivery
4. **API Integration**: Azure Functions backend (optional)

### Manual Deployment
```bash
# Build for production
dotnet publish -c Release -o ./publish

# Deploy the contents of ./publish/wwwroot/
```

## 🔒 Security Features

- **Authentication**: Azure AD B2C integration
- **Authorization**: Role-based access control
- **Token Management**: Secure token storage and refresh
- **Input Validation**: Client and server-side validation
- **File Type Validation**: Whitelist-based file filtering
- **Size Limits**: Configurable file size restrictions

## 📊 Performance Optimizations

- **WebAssembly**: Client-side processing for PDF operations
- **Lazy Loading**: Component-based lazy loading
- **Memory Management**: Proper stream disposal in WebAssembly
- **Caching**: Browser caching for static assets
- **Compression**: Gzip compression for published assets

## 🧪 Testing

The application includes comprehensive error handling and validation:

- **File validation**: Format and size checking
- **Stream management**: Proper resource disposal
- **Error boundaries**: Graceful error handling
- **Console logging**: Detailed debugging information

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎯 Roadmap

### Planned Features
- [ ] Bulk file operations
- [ ] PDF annotation tools
- [ ] Document templates
- [ ] OCR integration
- [ ] Collaborative editing
- [ ] Mobile app (MAUI)

### Technical Improvements
- [ ] Unit test coverage
- [ ] Integration tests
- [ ] Performance monitoring
- [ ] Docker containerization
- [ ] Kubernetes deployment

## 📞 Support

For questions, issues, or contributions:

- **GitHub Issues**: [Report bugs or request features](https://github.com/manishmawat/doc-uploader/issues)
- **Documentation**: Check the inline code documentation
- **Community**: Join discussions in GitHub Discussions

## 🙏 Acknowledgments

- [Microsoft FluentUI](https://github.com/microsoft/fluentui) - Design system
- [iText7](https://github.com/itext/itext7-dotnet) - PDF processing library
- [Blazor WebAssembly](https://docs.microsoft.com/en-us/aspnet/core/blazor/) - Framework
- [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/) - Hosting platform

---

Built with ❤️ using Blazor WebAssembly and Microsoft FluentUI
