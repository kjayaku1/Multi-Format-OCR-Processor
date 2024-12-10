## OCR API Documentation 🖼️✨**

## 📽️ Live Demo
http://137.184.77.186:4000/api-docs/

## ⚙️ Features
- 📄 Text Extraction: Extract text from images and scanned PDFs, supporting multiple formats.
- 📊 Table Extraction: Extract structured table data from PDFs and return it in JSON format.
- 🌍 Multi-language Support: Recognizes text and tables in various languages and handles special characters.

## Endpoints 🛣️
**/ocr/table-to-json 📊**
**Description**: Extract text from an uploaded image.
**Features**
- Supports text extraction for images and scanned PDFs.
- Handles multiple languages with 80-90% accuracy depending on input quality.
- Outputs text as a JSON object, preserving the structure of the original text
**Request Details**
Method: POST
Supported Formats: PDF (Only PDFs containing tables)



**Prerequisites**
Node.js and npm installed.
Azure Cognitive Services OCR subscription.
Git installed for version control.

## 📌 Table of Contents
1. [Project Setup](#project-setup)
2. [API Endpoints](#api-endpoints)
3. [Error Handling](#error-handling)
4. [Usage Examples](#usage-examples)
5. [Environment Variables](#environment-variables)
6. [Testing](#testing)
7. [Technologies Used](#technologies-used)
8. [FAQ](#faq)
9. [Acknowledgements](#acknowledgements)

---

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

---
<h2 id="api-endpoints">🌐 API Endpoints</h2>
Details about the API endpoints.
### Base URL
```bash
http://localhost:3000/api/ocr
```

---

### 1. `POST /`
**Description**: Extract text from an uploaded image.


#### Request
- **Method**: `POST`
- **Body**: `form-data`
  - **Key**: `file` (type: **File**)


#### Response
```json
{
    "language": "en",
    "regions": [
        {
            "boundingBox": "42,42,551,551",
            "lines": [
                {
                    "words": [
                        { "text": "Hello" },
                        { "text": "World" }
                    ]
                }
            ]
        }
    ]
}
```

## 2. `GET /status`

**Description:** Check the API status and uptime.

### Response
```json
{
  "status": "API is running",
  "uptime": "52.34 seconds",
  "timestamp": "2024-12-05T12:34:56.789Z"
}
```

## 3. `POST /extract-region`

**Description:** Extract text from a specific region in an image.

### Request

- **Method:** `POST`
- **Body:** `form-data`
  - **Key:** `file` (type: File)
  - **Key:** `x`, `y`, `width`, `height` (integer)

### Response
```json
{
  "extractedText": "This is a test text"
}
```
## 4. `POST /reverse-text`

**Description:** Reverse the extracted text.

### Request

- **Method:** `POST`
- **Body:** `form-data`
  - **Key:** `file` (type: File)

### Response
```json
{
  "originalText": "Hello World",
  "reversedText": "dlroW olleH"
}
```
<h2 id="error-handling">🛑 Error Handling</h2>
How errors are handled in the project.

The API returns consistent error responses for various scenarios:

### 400 Bad Request
**Cause:** Missing or invalid input.

#### Example Response:
```json
{
  "error": "No file uploaded. Please upload an image."
}
```
### 500 Internal Server Error

**Cause:** Server-side issues.

#### Response:
```json
{
  "error": "Failed to process the image. Please try again."
}
```
<h2 id="usage-examples">💠 Usage Examples</h2>
Examples of how to use the API.

### Example Using `curl`
```bash
curl -X POST -F "file=@sample.jpg" http://localhost:3000/api/ocr/
```
### Postman Setup
- Import the API endpoints into Postman from Swagger.
- Test the endpoints interactively.

<h2 id="environment-variables">🌐 Environment Variables</h2>
Details about required environment variables.

The following environment variables are required:

- `PORT`: Port on which the API runs (default: `3000`).
- `AZURE_API_KEY`: Your Azure Cognitive Services API Key.
- `AZURE_ENDPOINT`: Endpoint URL for Azure Cognitive Services.

<h2 id="testing">👩🏻‍💻 Testing</h2>
Instructions for testing the project.

## 1. Local Testing

- **Start the server:**
  ```bash
  node app.js
   ```
- Test with Swagger UI: http://localhost:3000/api-docs

## 2. Production Testing

- Deploy to a cloud platform (e.g., DigitalOcean, AWS).
- Test the API using the deployed URL.

<h2 id="technologies-used">📊 Technologies Used</h2>
Technologies used in the project.

- **Backend:** Node.js, Express.js
- **OCR:** Azure Cognitive Services
- **Documentation:** Swagger UI
- **Process Manager:** PM2
- **Deployment:** DigitalOcean

<h2 id="faq">📬 FAQ</h2>
Frequently asked questions.

1. **What file formats are supported?**  
   The API supports `.jpg`, `.jpeg`, `.png`, and `.bmp` file formats.

2. **How do I deploy this API?**  
   Follow the deployment guide provided in the [Project Setup](#project-setup) section.

3. **What happens if no text is found?**  
   The API will return a response with `"extractedText": ""`.

4. **How about quality of the image?**  
   The image should be of some decent quality in order for OCR to process it smoothly.

<h2 id="acknowledgements">⚜️ Acknowledgements</h2>
Acknowledgements for contributions or references.

- **Azure Cognitive Services** for powering the OCR functionality.
- **Swagger UI** for interactive API documentation.
- **DigitalOcean** for hosting.

