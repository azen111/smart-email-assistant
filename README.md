# Smart Email Assistant

An AI-powered email reply assistant built with **Java, Spring Boot, Spring AI, Google Gemini, React, and a browser extension**.

The application generates context-aware email replies from the provided email content and a selected tone, with a React web interface and browser-extension integration.

## Features

- 🤖 **AI-Powered Email Replies**  
  Generate context-aware email responses using Google Gemini through Spring AI.

- 🎯 **Tone Selection**  
  Generate replies based on the desired communication tone, such as professional or casual.

- 🔌 **REST API**  
  Spring Boot backend exposes an API for generating AI-powered email responses.

- ⚛️ **React Frontend**  
  Web interface for entering email content, selecting a tone, and generating a response.

- 🌐 **Browser Extension**  
  Provides email-reply assistance directly within the browser.

## Tech Stack

### Backend
- Java 17+
- Spring Boot
- Spring AI
- REST APIs
- Maven

### AI
- Google Gemini API
- Spring AI

### Frontend
- React
- JavaScript
- HTML
- CSS
- Vite

### Browser Extension
- JavaScript
- HTML
- CSS
- Chrome Extension APIs

## Project Structure

```text
smart-email-assistant/
│
├── src/
│   └── main/
│       ├── java/com/email/writer/
│       │   ├── EmailWriterApplication.java
│       │   └── app/
│       │       ├── EmailGeneratorController.java
│       │       ├── EmailGeneratorService.java
│       │       └── EmailRequest.java
│       │
│       └── resources/
│           └── application.properties
│
├── email-writer-react/
│   ├── src/
│   ├── package.json
│   └── vite.config.js
│
├── Email-Reply-Extension/
│   ├── content.js
│   ├── content.css
│   ├── popup.html
│   ├── script.js
│   └── manifest.json
│
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

## How It Works

```text
User enters email content
          │
          ▼
    React Frontend
          │
          │ HTTP POST
          ▼
 Spring Boot REST API
          │
          ▼
 Email Generator Service
          │
          ▼
      Spring AI
          │
          ▼
    Google Gemini
          │
          ▼
    Generated Reply
          │
          ▼
    React / Extension
```

## API

### Generate Email Reply

**Endpoint**

```http
POST /api/email/generate
```

**Request**

```json
{
  "emailContent": "Hi, I'm following up on our meeting last week. When can we expect the project deliverables?",
  "tone": "professional"
}
```

**Response**

The API returns an AI-generated email reply based on the supplied email content and requested tone.

### Example using cURL

```bash
curl -X POST "http://localhost:9191/api/email/generate" \
-H "Content-Type: application/json" \
-d '{
  "emailContent": "Hi, I am following up on our meeting last week. When can we expect the project deliverables?",
  "tone": "professional"
}'
```

## Getting Started

### Prerequisites

Make sure you have:

- Java 17 or later
- Maven 3.9+ (optional when using the included Maven wrapper)
- Node.js and npm
- A Google Gemini API key

### 1. Clone the repository

```bash
git clone https://github.com/azen111/smart-email-assistant.git
cd smart-email-assistant
```

### 2. Configure the Gemini API

The application reads the Gemini configuration from environment variables.

Set:

```text
GEMINI_URL=<your-gemini-api-url>
GEMINI_KEY=<your-gemini-api-key>
```

Do **not** commit your API key to GitHub.

The application expects these variables through:

```properties
gemini.api.url=${GEMINI_URL}
gemini.api.key=${GEMINI_KEY}
```

### 3. Run the Spring Boot backend

On Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

Or, if Maven is installed:

```bash
mvn spring-boot:run
```

The backend runs on:

```text
http://localhost:9191
```

### 4. Run the React frontend

Open another terminal:

```bash
cd email-writer-react
npm install
npm run dev
```

Vite will provide the local frontend URL in the terminal.

## Browser Extension

The project also contains a browser extension in:

```text
Email-Reply-Extension/
```

To load it in Chrome:

1. Open Chrome.
2. Navigate to `chrome://extensions`.
3. Enable **Developer mode**.
4. Select **Load unpacked**.
5. Select the `Email-Reply-Extension` directory.
6. Enable the extension.

## Environment Variables

| Variable | Description |
|---|---|
| `GEMINI_URL` | Google Gemini API endpoint |
| `GEMINI_KEY` | Google Gemini API key |

Keep credentials outside the repository. Never commit API keys, passwords, or other secrets.

## Future Improvements

- Improve error handling and validation
- Add authentication and user accounts
- Add persistent email history
- Improve browser-extension integration
- Add automated backend and frontend tests
- Deploy the backend and frontend for public access

## License

This project is intended as a portfolio and learning project.
