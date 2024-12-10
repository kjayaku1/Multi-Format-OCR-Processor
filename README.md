## OCR API Documentation 🖼️✨**

## 📽️ Live Demo
http://137.184.77.186:4000/api-docs/

## ⚙️ Main Features
- 📄 Text Extraction: Extract text from images and scanned PDFs, supporting multiple formats.
- 📊 Table Extraction: Extract structured table data from PDFs and return it in JSON format.
- 🌍 Multi-language Support: Recognizes text and tables in various languages and handles special characters.

## Endpoints 🛣️
**1. /ocr/table-to-json 📊**

**Description**: Extract text from an uploaded image.

**Features**
- Supports text extraction for images with text, handwritten notes,  and scanned PDFs.
- Handles multiple languages with 80-90% accuracy depending on input quality example(chinese).
- Outputs text as a JSON object, preserving the structure of the original text

#### **Request Details**
- **Method**: `POST`
- **Content-Type**: `multipart/form-data`
- **Supported Formats**: `JPEG`, `PNG`, `BMP`, `TIFF`, `PDF`

**2. /ocr/table-to-json**

**Description**: Extracts table data from PDF documents and returns it as JSON.

**Features**
- Extracts tables with rows and columns into a JSON format.
- Supports multi-language content and special characters.

#### **Request Details**
- **Method**: `POST`
- **Content-Type**: `multipart/form-data`
- **Supported Formats**: `PDF`

## Getting Started 💻

**Prerequisites**
- Node.js and npm installed.
- Azure Cognitive Services OCR subscription.
- Git installed for version control.

<h2 id="project-setup">🛠️ Project Setup</h2>
Instructions for setting up the project.

### Prerequisites
- **Node.js** and **npm** installed.
- Azure Cognitive Services OCR subscription.
- Git installed for version control.

### Installation
1. Clone the repository:
   ```bash
   git clone <your_repo_url>
   cd azure-ocr-api

2. Install Dependencies
   ```bash
   npm install axios body-parser curl dotenv express multer node pm2 swagger-jsdoc swagger-ui-express

3. Set up the environmental variables:
   - create a `.env` file
   ```bash 
   AZURE_API_KEY=your_azure_api_key
   AZURE_ENDPOINT=https://your-azure-endpoint.cognitiveservices.azure.com/
   PORT=3000
4. Start the server
   ```bash
   pm2 start app.js

   <h2 id="inserted api-endpoints">🌐 Inserted API Endpoints</h2>
Details about the API endpoints.
### Base URL
```bash
http://localhost:4000/api/ocr
```

---

### 1. `POST /`
**Description**: Extract text from an the image.


#### Request
- **Method**: `POST`
- **Body**: `form-data`
  - **Key**: `file` (type: **File**)

