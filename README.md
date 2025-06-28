# Brochure Web Portal

A modern web application that allows users to upload PDF brochures, extract items and prices using OCR technology, and search across all uploaded content.

## Features

### 🚀 Core Functionality
- **Multi-file Upload**: Upload multiple PDF brochures simultaneously
- **OCR Processing**: Extract text and images from PDFs using Tesseract OCR
- **Smart Search**: Search for items by name or price across all brochures
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices

### 🎨 User Interface
- **Modern UI**: Clean, intuitive interface with gradient backgrounds and card-based design
- **Real-time Feedback**: Upload progress indicators and status messages
- **Search Results**: Beautiful grid layout displaying items with images and prices
- **Navigation**: Easy switching between upload and search functionality

### 🔧 Technical Features
- **Django REST API**: Robust backend with RESTful endpoints
- **React Frontend**: Modern React application with hooks and functional components
- **Image Processing**: Automatic image extraction and optimization
- **Database Storage**: SQLite database (easily configurable for PostgreSQL/MySQL)

## Tech Stack

### Backend
- **Django 5.2.3**: Web framework
- **Django REST Framework**: API development
- **PyMuPDF**: PDF processing and image extraction
- **Tesseract OCR**: Text recognition from images
- **Pillow**: Image processing and optimization
- **SQLite**: Database (default)

### Frontend
- **React 19.1.0**: UI framework
- **Axios**: HTTP client for API communication
- **CSS3**: Modern styling with gradients and animations

## Prerequisites

### System Requirements
- Python 3.8+
- Node.js 16+
- Tesseract OCR installed on your system

### Tesseract Installation

#### Windows
1. Download Tesseract from: https://github.com/UB-Mannheim/tesseract/wiki
2. Install to `C:\Program Files\Tesseract-OCR\`
3. Add to PATH environment variable

#### macOS
```bash
brew install tesseract
```

#### Ubuntu/Debian
```bash
sudo apt-get install tesseract-ocr
```

## Installation & Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd project
```

### 2. Backend Setup (Django)

```bash
cd ocr-brochure-portal

# Create virtual environment
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser (optional)
python manage.py createsuperuser

# Start development server
python manage.py runserver
```

The Django backend will be available at `http://localhost:8000`

### 3. Frontend Setup (React)

```bash
cd brochure-frontend

# Install dependencies
npm install

# Start development server
npm start
```

The React frontend will be available at `http://localhost:3000`

## Usage

### Uploading Brochures
1. Navigate to the "Upload Brochures" tab
2. Optionally enter a default title for your brochures
3. Select one or more PDF files
4. Click "Upload Brochures"
5. Wait for OCR processing to complete

### Searching Items
1. Navigate to the "Search Items" tab
2. Enter your search query (item name or price)
3. Press Enter or click "Search"
4. Browse through the results displayed in a grid layout

## API Endpoints

### Upload Brochure
- **POST** `/api/upload/`
- **Content-Type**: `multipart/form-data`
- **Parameters**: 
  - `file`: PDF file
  - `title`: Brochure title (optional)

### Search Items
- **GET** `/api/search/?q=<query>`
- **Parameters**:
  - `q`: Search query string

### List Brochures
- **GET** `/api/brochures/`
- Returns list of all uploaded brochures

## Project Structure

```
project/
├── brochure-frontend/          # React frontend
│   ├── src/
│   │   ├── components/         # React components
│   │   │   ├── UploadForm.jsx
│   │   │   └── SearchComponent.jsx
│   │   ├── App.js             # Main app component
│   │   └── App.css            # Main styles
│   └── package.json
├── ocr-brochure-portal/        # Django backend
│   ├── ocrdata/               # Main Django app
│   │   ├── models.py          # Database models
│   │   ├── views.py           # API views
│   │   └── urls.py            # URL routing
│   ├── ocr_portal/            # Django project settings
│   └── requirements.txt       # Python dependencies
└── README.md
```

## Configuration

### Database
The application uses SQLite by default. To use PostgreSQL or MySQL:

1. Update `DATABASES` in `ocr_portal/settings.py`
2. Install appropriate database adapter
3. Run migrations

### CORS Settings
CORS is configured for development. For production, update `CORS_ALLOWED_ORIGINS` in `settings.py`.

### Tesseract Path
If Tesseract is installed in a different location, update the path in `ocrdata/views.py`:
```python
pytesseract.pytesseract.tesseract_cmd = r"path/to/tesseract.exe"
```

## Development

### Running Tests
```bash
# Backend tests
cd ocr-brochure-portal
python manage.py test

# Frontend tests
cd brochure-frontend
npm test
```

### Code Style
- Backend: Follow PEP 8 guidelines
- Frontend: Use ESLint and Prettier

## Deployment

### Production Considerations
1. **Database**: Use PostgreSQL or MySQL for production
2. **Static Files**: Configure proper static file serving
3. **Media Files**: Use cloud storage (AWS S3, etc.) for media files
4. **Security**: Update `SECRET_KEY` and disable `DEBUG`
5. **CORS**: Configure allowed origins for production domain

### Environment Variables
Create a `.env` file for sensitive configuration:
```
SECRET_KEY=your-secret-key
DEBUG=False
ALLOWED_HOSTS=your-domain.com
```

## Troubleshooting

### Common Issues

1. **Tesseract not found**
   - Ensure Tesseract is installed and in PATH
   - Update the path in `views.py`

2. **CORS errors**
   - Check CORS settings in `settings.py`
   - Ensure frontend URL is in `CORS_ALLOWED_ORIGINS`

3. **Upload failures**
   - Check file size limits
   - Ensure PDF files are valid
   - Check media directory permissions

4. **Search not working**
   - Verify database migrations are applied
   - Check if brochures have been uploaded and processed

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License.

## Support

For issues and questions:
1. Check the troubleshooting section
2. Review the documentation
3. Create an issue in the repository

---

**Note**: This application is designed for educational and development purposes. For production use, ensure proper security measures and performance optimizations are implemented. 