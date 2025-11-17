# SmartSheetConnect

**Full-stack TypeScript lead capture platform** | Production-ready | Google Sheets integration

[![TypeScript](https://img.shields.io/badge/TypeScript-5.6+-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18.3+-61DAFB?style=flat&logo=react&logoColor=white)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.21+-000000?style=flat&logo=express&logoColor=white)](https://expressjs.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Testing](https://img.shields.io/badge/Testing-33%20Tests-green.svg)](#testing--quality-assurance)
[![Security](https://img.shields.io/badge/Security-Headers%20%7C%20Rate%20Limited%20%7C%20Honeypot-brightgreen.svg)](#security-implementation)
[![Google APIs](https://img.shields.io/badge/Google%20APIs-Sheets%20%7C%20Drive%20%7C%20Gmail-blue.svg)](#tech-stack)

![Visitor Count](https://visitor-badge.laobi.icu/badge?page_id=lindseystead.smartsheet-connect)

![Last Commit](https://img.shields.io/github/last-commit/lindseystead/SmartSheetConnect)

**Live Demo:** Coming Soon

> **Note:** Developed as a production-ready full-stack application with complete backend, frontend, and Google Cloud integration. This application automatically logs form submissions to Google Sheets and sends real-time notifications via email and Slack.

---

## 📸 Screenshots

### Landing Page
![Landing Page](./assets/screenshot-landing.png)
*Modern landing page with hero section, features overview, and lead capture form*

### Contact Form
![Contact Form](./assets/screenshot-form.png)
*Lead capture form with real-time validation and Google Sheets integration*

### How It Works
![How It Works](./assets/screenshot-howitworks.png)
*Visual explanation of the automated lead capture and logging process*

---

## 🎯 What It Does

Production-ready lead capture platform that automatically logs form submissions to Google Sheets and sends real-time notifications. Features intelligent spreadsheet management, spam protection, and seamless Google Cloud integration.

**Impact:**
- **Zero manual data entry** - All leads automatically logged to Google Sheets
- **Intelligent spreadsheet management** - Auto-creates and reuses spreadsheets
- **Real-time notifications** - Email and Slack alerts for new submissions
- **Enterprise-ready** - Production-grade security and error handling
- **Developer-friendly** - TypeScript throughout with comprehensive testing

---

## 📊 By The Numbers

| Metric | Value |
|--------|-------|
| **Codebase** | 60+ TypeScript files, 5,000+ lines |
| **API Endpoints** | 2 RESTful endpoints |
| **Service Integrations** | 4 core services (Google Sheets, Gmail, Slack, Storage) |
| **UI Components** | 55+ React components (including shadcn/ui) |
| **Test Coverage** | 33 comprehensive tests |
| **Security** | Security headers (Helmet.js), honeypot spam protection, rate limiting |
| **Google APIs** | Sheets, Drive, Gmail integration |

---

## 🏗️ Architecture

**Full-Stack TypeScript with Express Backend and React Frontend**

```
┌─────────────────────────────────┐
│  Frontend (React 18)            │  Vite | React Hook Form | Zod
│  - Lead Capture Form            │  TanStack Query | Tailwind CSS
│  - Real-time Validation         │  shadcn/ui Components
└──────────────┬──────────────────┘
               │ HTTP/REST
┌──────────────▼──────────────────┐
│  Backend (Express + TypeScript) │  Express | TypeScript | Zod
│  - API Routes                    │  Rate Limiting | Helmet.js
│  - Request Validation            │  CORS | Compression
└──────────────┬──────────────────┘
               │
┌──────────────▼──────────────────┐
│  Services Layer                  │
│  ┌────────────────────────────┐ │
│  │ Storage Service            │ │  Google Sheets Integration
│  │ Email Service              │ │  Gmail API
│  │ Slack Service              │ │  Webhooks
│  └────────────────────────────┘ │
└──────────────┬──────────────────┘
               │
┌──────────────▼──────────────────┐
│  Google Cloud APIs              │  Sheets API | Drive API | Gmail API
│  - OAuth2 Authentication         │  Auto-spreadsheet Management
│  - Spreadsheet Operations        │  Email Notifications
└─────────────────────────────────┘
```

**Key Design Decisions:**
- **TypeScript Throughout:** Type safety from frontend to backend
- **Zod Validation:** Runtime validation matching TypeScript types
- **Service Layer:** Clean separation of business logic
- **Auto-Spreadsheet Management:** Intelligent creation and reuse
- **Non-blocking Notifications:** Email/Slack failures don't break submissions
- **Production-Ready:** Comprehensive error handling and logging

---

## 🛠️ Tech Stack

**Backend:** Node.js 18+ | Express 4.21+ | TypeScript 5.6+ | Google APIs (Sheets, Drive, Gmail) | OAuth2

**Frontend:** React 18.3+ | TypeScript | Vite 7+ | React Hook Form | Zod | TanStack Query | Tailwind CSS | shadcn/ui

**Testing:** Vitest | React Testing Library | Supertest | 33 comprehensive tests

**Security:** Helmet.js | express-rate-limit | CORS | Honeypot spam protection | Input validation

**DevOps:** Vite build | esbuild bundling | Environment variables | Railway deployment ready

**Integrations:** Google Sheets API | Google Drive API | Gmail API | Slack Webhooks

---

## 🔒 Security Implementation

- ✅ **Security Headers:** Helmet.js with Content Security Policy and secure HTTP headers
- ✅ **SQL Injection Prevention:** N/A (NoSQL/API-based, no raw queries)
- ✅ **XSS Prevention:** React's built-in XSS protection + input sanitization
- ✅ **Rate Limiting:** 100 requests per 15 minutes per IP address
- ✅ **Honeypot Spam Protection:** Hidden field detection for bot filtering
- ✅ **Input Validation:** Zod schemas on both client and server
- ✅ **Request Size Limits:** 10MB maximum payload size
- ✅ **Environment Variables:** All sensitive data in `.env` (never committed)
- ✅ **OAuth2 Security:** Secure token refresh and credential management

---

## 🗄️ Google Sheets Integration

**Intelligent spreadsheet management with automatic creation and reuse.**

### Spreadsheet Management

- **Auto-Creation:** Creates spreadsheet on first submission if none exists
- **Auto-Discovery:** Searches for existing spreadsheet by organization name
- **Auto-Persistence:** Automatically saves `SPREADSHEET_ID` to `.env` file
- **Manual Override:** Set `SPREADSHEET_ID` in `.env` for specific spreadsheet
- **Duplicate Prevention:** Always reuses same spreadsheet across server restarts

### Spreadsheet Structure

- **Sheet Name:** `Leads`
- **Columns:** Timestamp | Name | Email | Phone | Message
- **Title Format:** `SmartSheetConnect - [Organization Name] - Website Form Leads`
- **Organization Name:** Uses `ORGANIZATION_NAME` or `COMPANY_NAME` from `.env`

### Key Features

- Automatic header row creation on new spreadsheets
- Human-readable timestamp formatting
- Row number tracking for reference
- Error handling with graceful fallbacks
- Drive API integration for spreadsheet discovery

**See:** `server/services/googleSheets.ts` for complete implementation

---

## 🧪 Testing & Quality Assurance

**Comprehensive testing approach ensuring production-ready reliability.**

### Testing Methodology

- **Unit Tests:** Schema validation, service functions
- **Integration Tests:** API endpoint testing with Supertest
- **Component Tests:** React component behavior with React Testing Library
- **Security Testing:** Honeypot validation, rate limiting verification
- **Error Handling:** Comprehensive error scenario coverage

### Test Coverage

✅ **Schema Validation:** 15 tests covering all validation rules  
✅ **API Endpoints:** 8 tests for `/api/submit-lead` and `/api/health`  
✅ **React Components:** 10 tests for form behavior and user interactions  
✅ **Security:** Honeypot detection, validation errors, spam protection  
✅ **Error Handling:** Storage failures, API errors, network issues  

### Quality Metrics

- **Test Count:** 33 comprehensive tests
- **Code Quality:** TypeScript strict mode, consistent structure
- **Security:** Security headers (Helmet.js), zero SQL injection vulnerabilities, comprehensive input validation
- **Performance:** Optimized API calls, efficient spreadsheet operations
- **Maintainability:** Clean architecture, separation of concerns, reusable components

**Run Tests:**
```bash
npm test              # Watch mode
npm run test:coverage # With coverage report
npm run test:run      # CI mode (single run)
```

---

## 💼 Engineering Skills Demonstrated

- **Full-Stack Development:** React frontend + Express backend with TypeScript
- **API Integration:** Google Sheets, Drive, and Gmail APIs with OAuth2
- **Type Safety:** End-to-end TypeScript with Zod runtime validation
- **Security:** Security headers (Helmet.js), rate limiting, honeypot spam protection, input validation
- **Testing:** Comprehensive test suite with Vitest, React Testing Library, Supertest
- **User Experience:** Real-time form validation, responsive design, intuitive UI
- **DevOps:** Production builds, environment configuration, deployment ready
- **Error Handling:** Graceful error handling, non-blocking notifications
- **Code Quality:** Professional documentation, consistent structure, type safety
- **Third-Party Integration:** Google Cloud APIs, Slack webhooks, OAuth2 flows

---

## 📁 Project Structure

```
SmartSheetConnect/
├── client/                    # React frontend
│   ├── src/
│   │   ├── components/       # React components
│   │   │   ├── ui/           # shadcn/ui components (55+ files)
│   │   │   ├── DemoFormSection.tsx
│   │   │   ├── FeaturesSection.tsx
│   │   │   ├── Footer.tsx
│   │   │   ├── Header.tsx
│   │   │   ├── HeroSection.tsx
│   │   │   ├── HowItWorksSection.tsx
│   │   │   └── SocialProofSection.tsx
│   │   ├── hooks/            # Custom React hooks
│   │   ├── lib/              # Utilities (queryClient, utils)
│   │   ├── pages/            # Page components
│   │   └── main.tsx         # Entry point
│   └── index.html
├── server/                    # Express backend
│   ├── services/             # Business logic services
│   │   ├── email.ts          # Gmail API integration
│   │   ├── googleSheets.ts   # Google Sheets operations
│   │   ├── slack.ts          # Slack webhook integration
│   │   └── storage.ts        # Storage interface
│   ├── routes.ts             # API endpoints
│   ├── index.ts              # Server entry point
│   └── utils/                # Server utilities
├── shared/                    # Shared code
│   ├── schema.ts             # Zod schemas
│   └── schema.test.ts        # Schema tests
├── assets/                    # Images and screenshots
└── package.json
```

---

## 🚀 Quick Start

```bash
# 1. Clone repository
git clone https://github.com/lindseystead/SmartSheetConnect.git
cd SmartSheetConnect/SmartSheetConnect

# 2. Install dependencies
npm install

# 3. Configure environment variables
# Create .env file with:
#   GOOGLE_CLIENT_ID=your-client-id
#   GOOGLE_CLIENT_SECRET=your-client-secret
#   GOOGLE_REFRESH_TOKEN=your-refresh-token
#   NOTIFICATION_EMAIL=your-email@example.com
#   ORGANIZATION_NAME=Your Company Name
#   (See Configuration section below for full list)

# 4. Start development server
npm run dev

# 5. Visit http://localhost:5000
```

**For detailed setup instructions, see [Configuration](#configuration) section below.**

---

## ⚙️ Configuration

### Prerequisites

- Node.js 18+ and npm
- Google Cloud account
- Google Cloud project with APIs enabled

### Google Cloud Setup
   
   **Step 1: Create Project & Enable APIs**
   - Create a Google Cloud project at [console.cloud.google.com](https://console.cloud.google.com)
   - Enable required APIs:
     - **Google Sheets API** (required) - [Enable](https://console.cloud.google.com/apis/library/sheets.googleapis.com)
     - **Google Drive API** (recommended) - [Enable](https://console.cloud.google.com/apis/library/drive.googleapis.com)
     - **Gmail API** (optional, for email notifications) - [Enable](https://console.cloud.google.com/apis/library/gmail.googleapis.com)
   
   **Step 2: Create OAuth Credentials**
   - Go to "APIs & Services" → "Credentials"
   - Click "Create Credentials" → "OAuth client ID"
   - If prompted, configure OAuth consent screen first
   - Application type: "Web application"
   - Copy your **Client ID** and **Client Secret**
   
   **Step 3: Generate Refresh Token**
   - Go to [OAuth 2.0 Playground](https://developers.google.com/oauthplayground/)
   - Click **Settings** (gear icon) → Check **"Use your own OAuth credentials"**
   - Enter your **Client ID** and **Client Secret**
   - In **Step 1**, select these scopes:
     - `https://www.googleapis.com/auth/spreadsheets`
     - `https://www.googleapis.com/auth/drive`
     - `https://www.googleapis.com/auth/gmail.send` (if using email notifications)
   - Click **"Authorize APIs"** and sign in with your Google account
   - In **Step 2**, click **"Exchange authorization code for tokens"**
   - Copy the **Refresh token** (starts with `1//0...`)

### Environment Variables
   
Create `.env` file in project root:
   
   ```env
   # Required
   GOOGLE_CLIENT_ID=your-client-id
   GOOGLE_CLIENT_SECRET=your-client-secret
   GOOGLE_REFRESH_TOKEN=your-refresh-token
   NOTIFICATION_EMAIL=your-email@example.com

   # Optional
ORGANIZATION_NAME=Your Company Name  # or use COMPANY_NAME (both supported)
SPREADSHEET_ID=existing-spreadsheet-id  # Auto-saved after first creation
   SLACK_WEBHOOK_URL=https://hooks.slack.com/services/...
   PORT=5000
   HOST=localhost
   ALLOWED_ORIGINS=https://yoursite.com
   ```

### Slack Setup (Optional)

1. Create Slack app at [api.slack.com/apps](https://api.slack.com/apps)
2. Enable "Incoming Webhooks" feature
3. Add webhook to workspace and copy URL
4. Add to `.env` as `SLACK_WEBHOOK_URL`

### Need Setup Help?

Setting up Google Cloud credentials and deploying can be complex. **Professional setup services are available:**

- ✅ Google Cloud project configuration
- ✅ OAuth credentials setup
- ✅ Railway deployment assistance
- ✅ Testing and verification
- ✅ Custom domain configuration (optional)

**Contact:** [info@lifesavertech.ca](mailto:info@lifesavertech.ca) or visit [lifesavertech.ca](https://www.lifesavertech.ca)

For commercial licensing options, see [LICENSING.md](./LICENSING.md).

---

## 📡 API Endpoints

### `POST /api/submit-lead`

Submits a new lead submission.

**Request:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "(555) 123-4567",  // optional
  "message": "Interested in your services"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Lead submitted successfully",
  "rowNumber": 2
}
```

**Error Responses:**
- `400` - Validation error (invalid input data)
- `429` - Too many requests (rate limited)
- `500` - Server error (internal error)

### `GET /api/health`

Returns server health status.

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2025-01-20T15:30:00.000Z",
  "uptime": 3600
}
```

---

## 🚢 Deployment

### Railway Deployment (Quick Start)

1. **Push to GitHub** - Ensure your code is in a GitHub repository
2. **Create Railway Account** - Go to [railway.app](https://railway.app) and sign up
3. **Deploy from GitHub** - Connect your repository
4. **Add Environment Variables** - Copy all variables from your `.env` file to Railway's Variables tab
5. **Deploy** - Railway automatically builds and deploys

---

## 🔐 Code Access

**This is open-source software under MIT License.** Source code is available for use, modification, and distribution.

**For Portfolio Review:**
- ✅ **Code Review:** Full codebase available on GitHub
- ✅ **Code Inspection:** Feel free to inspect the codebase
- ✅ **Interview Discussion:** Project can be discussed in interviews
- ✅ **Learning Resource:** Use as reference for similar projects

**For Commercial Use:**
- This software is available under MIT License for commercial use
- Commercial licensing options available for enterprise features
- Setup and support services available
- **Licensing inquiries:** Lifesaver Technology Services (info@lifesavertech.ca)

---

## 📄 License & Intellectual Property

**License:** MIT License - see [LICENSE](LICENSE) file.

**Intellectual Property:** This project was designed, created, and implemented by **Lindsey D. Stead** (sole proprietor of Lifesaver Technology Services).

**Copyright © 2025 Lindsey D. Stead. All Rights Reserved.**

**Business Licensing:** Lifesaver Technology Services is the authorized agent for commercial licensing, setup services, and support inquiries.

**Open Source Project** - This repository is available under MIT license for portfolio, learning, and commercial use.

**For Recruiters & Hiring Managers:**
- ✅ **Portfolio Review:** Feel free to review this code for evaluation purposes
- ✅ **Code Inspection:** You may inspect the codebase to assess technical skills
- ✅ **Interview Discussion:** This project can be discussed in interviews

**For Commercial Use:**
- This software is available under MIT License for open-source use
- Commercial licensing options available for enterprise features and support
- **Licensing inquiries:** Lifesaver Technology Services (info@lifesavertech.ca)

---

**Built with ❤️ for automated lead capture and seamless Google Sheets integration.**
