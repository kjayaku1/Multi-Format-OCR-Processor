## OCR API Documentation 🖼️✨**

This project provides an API for optical character recognition (OCR), allowing users to convert images to text and tables to JSON format. It includes comprehensive documentation for usage, testing, and installation.

## Technologies used: 
This project uses the following technologies:

1. **Node.js**: Server-side runtime environment for building the API.
2. **Express**: Web framework for routing and handling HTTP requests.
3. **Azure Cognitive Services OCR**: For optical character recognition and table extraction from images and PDFs.
4. **Swagger**: API documentation and UI for testing and interacting with the endpoints.
5. **Axios**: For making HTTP requests to the Azure OCR API.
6. **dotenv**: For managing environment variables in configuration files.

## Table of Contents
1. [Live Demo](#live-demo)
2. [Main Features](#main-features)
3. [Endpoints](#endpoints)
   - [/ocr/image-to-text](#1-post-ocrimage-to-text)
   - [/ocr/table-to-json](#2-post-ocrtable-to-json)
4. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
5. [API Usage](#api-usage)
6. [Postman Testing](#postman-testing)
7. [Localhost Testing](#localhost-testing)
8. [Live Testing](#live-testing)
9. [Error Handling](#error-handling)
10. [Testing with Screenshots](#Testing-with-screenshots)
11. [for reference](#for-reference)

## 1.📽️ Live Demo
http://137.184.77.186:4000/api-docs/

## 2. ⚙️ Main Features
- 📄 Text Extraction: Extract text from images and scanned PDFs, supporting multiple formats.
- 📊 Table Extraction: Extract structured table data from PDFs and return it in JSON format.
- 🌍 Multi-language Support: Recognizes text and tables in various languages and handles special characters.

## 3. Endpoints 🛣️
**1. /ocr/image-to-text 📊**

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

## 4.Getting Started 💻
### Prerequisites
- **Node.js** and **npm** installed.
- Azure Cognitive Services OCR subscription.
- Git installed for version control.

### Installation
1. Clone the repository:
   ```bash
   git clone <your_repo_url>
   cd (folder name)

2. Install Dependencies
   ```bash
  npm install axios body-parser curl dotenv express multer node pm2 swagger-jsdoc swagger-ui-express

3. Set up the environmental variables:
   create a `.env` file(I Have Used 2 .env files whihc is .env.local and .env.live)
   
- **.env.local**
   ```bash 
   APP_URL = http://localhost:4000
   PORT = 4000
   AZURE_API_ENDPOINT = https://si.cognitiveservices.azure.com
   AZURE_API_KEY = API KEY 1
   AZURE_API_KEY_TWO = API KEY 2

   AZURE_API_TABLE_TEXT_ENDPOINT = https://tabletotext.cognitiveservices.azure.com
   AZURE_API_TABLE_TEXT_KEY = API KEY 1
   AZURE_API_TABLE_TEXT_KEY_TWO = API KEY 2
   AZURE_API_REGION = eastus

- **.env.live**
   ```bash 
   APP_URL = http://137.184.77.186:4000
   PORT = 4000
   AZURE_API_ENDPOINT = https://si.cognitiveservices.azure.com
   AZURE_API_KEY = API KEY 1
   AZURE_API_KEY_TWO = API KEY 2

   AZURE_API_TABLE_TEXT_ENDPOINT = https://tabletotext.cognitiveservices.azure.com
   AZURE_API_TABLE_TEXT_KEY = API KEY 1
   AZURE_API_TABLE_TEXT_KEY_TWO = API KEY 2
   AZURE_API_REGION = eastus


4. To Start the server
   ```bash
   npm start app.js

![image](https://github.com/user-attachments/assets/4d887e31-ffbb-42a3-bbb6-2fcd7d9c7d11)

<h2 id="inserted api-endpoints">Used API Endpoints</h2>
Details about the API endpoints

### Base URL
```bash
http://localhost:4000/api-docs/
```
---

## 6.🧪 Postman testing  
### **How to Test with Postman**
Download the Postman and create one by adding the endpoints:
- /ocr/image-to-text
- /ocr/table-to-json

## 7.Localhost testing 
```bash 
node app.js
```
The server should be accessible at http://localhost:4000.

## 8.Live testing
Live Url:
```bash 
http://137.184.77.186:4000/api-docs/
```
## 9.❌ Error Handling  

The API gracefully handles the following errors:  

### **1. 400 - Bad Request**  

Possible reasons: - No file uploaded - Unsupported file format - No text could be extracted from the uploaded file. 

#### Example Response:  
```json

{
  "message": "No file was uploaded or file format is not supported."
}
```

### **2. 500 - Internal server error**  

Possible reasons: Internal server error, possibly related to Azure OCR API.

#### Example Response:  
```json
{
  "message": "Error occurred while processing the file with Azure OCR API."
}
```

### **3. 404 - No tables found in the document.**  

Possible reasons: No tables found in the document.

#### Example Response:  
```json
{
  "message": "No tables found in the document."
}
```
## 10. Testing with screenshots  
### 1. `POST /`
**Description**: Extract text from an the image.

#### Request
- **Method**: `POST`
- **Body**: `form-data`
- **Key**: `file` (type: **File**)
  
#### Response
```json
{
  "status": "success",
  "extractedText": "Hola world. This is OCR.",
  "detailedData": [
    {
      "page": 1,
      "line": 1,
      "text": "Hola world"
    }
  ]
}
```
#### Tested screenshots

I have uploaded the chinese language image:

![image](https://github.com/user-attachments/assets/7d2c6754-191f-4068-bfd7-5cbcc520f857)


### 2. `POST /`
**Description**:Extract table data from PDF to text

#### Request
- **Method**: `POST`
- **Body**: `form-data`
- **Key**: `file` (type: **File**)

#### Response
```json
{
  "status": "success",
  "tables": [
    {
      "header": [
        "Year",
        "Revenue ($)",
        "Expenses ($)",
        "Profit ($)"
      ],
      "body": [
        [
          "2021",
          "5,00,000",
          "3,00,000",
          "2,00,000"
        ]
      ]
    }
  ],
  "extractedData": [
    {}
  ]
}
```
#### Tested screenshots

I have uploaded the pdf whcich containes table

![image](https://github.com/user-attachments/assets/3f28ffde-f6df-4afe-8807-cd135b277c34)

---
### **3. For reference**  

Azure AI Optical Character Recognition (OCR)

https://azure.microsoft.com/en-us/products/ai-services/ai-vision/

Official documentation for Azure's OCR service, providing insights into using the OCR API for text and table extraction.
https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/overview-ocr

