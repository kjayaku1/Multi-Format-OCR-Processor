## OCR API Documentation 🖼️✨**

## 📽️ Live Demo
http://137.184.77.186:4000/api-docs/

## ⚙️ Features

-📄 Text Extraction: Extract text from images and scanned PDFs, supporting multiple formats.
-📊 Table Extraction: Extract structured table data from PDFs and return it in JSON format.
-🌍 Multi-language Support: Recognizes text and tables in various languages and handles special characters.
-⚡ Easy Integration: Simple-to-use endpoints for developers, with detailed Swagger documentation.

**Endpoints 🛣️**
**/ocr/image-to-text 🖼️**
Extracts text from images and scanned PDFs.

**Request Details**
Method: POST
Supported Formats: JPEG, PNG, BMP, TIFF, PDF
**Features**
Supports text extraction for images and scanned PDFs.
Handles multiple languages with 80-90% accuracy depending on input quality.
Outputs text as a JSON object, preserving the structure of the original text

**/ocr/table-to-json 📊**
Extracts table data from PDF documents and returns it as JSON.

**Request Details**
Method: POST
Supported Formats: PDF (Only PDFs containing tables)
**Features**
Extracts tables with rows and columns into a JSON format.
Supports multi-language content and special characters.

**Prerequisites**
Node.js and npm installed.
Azure Cognitive Services OCR subscription.
Git installed for version control.

