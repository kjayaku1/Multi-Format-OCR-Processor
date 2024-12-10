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
- **Content-Type**: `/form-data`
- **Supported Formats**: `JPEG`, `PNG`, `BMP`, `TIFF`, `PDF`

**2. /ocr/table-to-json**

**Description**: Extracts table data from PDF documents and returns it as JSON.

**Features**
- Extracts tables with rows and columns into a JSON format.
- Supports multi-language content and special characters.

#### **Request Details**
- **Method**: `POST`
- **Content-Type**: `/form-data`
- **Supported Formats**: `PDF`

## Getting Started 💻

**Prerequisites**
- Node.js and npm installed.
- Azure Cognitive Services OCR subscription.
- Git installed for version control.
