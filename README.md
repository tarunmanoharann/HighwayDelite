# Notes - Personal Note Management Platform

A modern, full-stack note-taking application built with security and user experience in mind. Features comprehensive authentication options including email-based OTP verification and Google OAuth integration.

## 🚀 Features

### Authentication & Security
- **Email Registration**: Secure user registration with OTP verification sent to email
- **Email Sign-In**: Passwordless authentication using one-time passwords
- **Google OAuth**: Seamless sign-up and sign-in with Google accounts
- **JWT Security**: All user sessions protected with JSON Web Tokens
- **Session Management**: Secure token-based authentication system

### Core Functionality
- **Note Management**: Create, view, and delete personal notes
- **Real-time Updates**: Instant synchronization of note changes
- **User Privacy**: Notes are private and accessible only to the authenticated user
- **Persistent Storage**: All data securely stored in MongoDB

### User Experience
- **Responsive Design**: Optimized for both desktop and mobile devices
- **Modern UI**: Clean interface built with Tailwind CSS
- **Fast Performance**: Built with Vite for optimal loading times
- **Type Safety**: Full TypeScript implementation on both frontend and backend

## 🛠 Technology Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Frontend** | React 18 + TypeScript | Component-based UI with type safety |
| **Build Tool** | Vite | Fast development and optimized builds |
| **Styling** | Tailwind CSS | Utility-first responsive design |
| **Backend** | Node.js + Express + TypeScript | RESTful API with type safety |
| **Database** | MongoDB + Mongoose | NoSQL document storage with ODM |
| **Authentication** | JWT + Google OAuth | Multi-factor authentication system |
| **Email Service** | Nodemailer | OTP delivery system |

## 📋 Prerequisites

Before setting up the project, ensure you have:

- **Node.js** (v16 or higher)
- **npm** or **yarn** package manager
- **MongoDB Atlas** account (or local MongoDB installation)
- **Google Cloud Console** project (for OAuth)
- **Gmail account** with App Password enabled

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd note-taking-app
```

### 2. Backend Configuration

Navigate to the backend directory:
```bash
cd note-app-server
```

Install dependencies:
```bash
npm install
```

Create environment configuration:
```bash
cp .env.example .env
```

Configure your `.env` file with the required variables (see [Environment Variables](#environment-variables) section).

Start the development server:
```bash
npm run dev
```

The backend API will be available at `http://localhost:5000`

### 3. Frontend Configuration

Navigate to the frontend directory:
```bash
cd note-app-client
```

Install dependencies:
```bash
npm install
```

Start the development server:
```bash
npm run dev
```

The frontend application will be available at `http://localhost:5173`

## 🔐 Environment Variables

Create a `.env` file in the `note-app-server` directory with the following configuration:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/<database-name>

# Authentication
JWT_SECRET=your-super-secure-jwt-secret-key-minimum-32-characters
JWT_EXPIRES_IN=7d

# Google OAuth Configuration
GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=your-google-client-secret

# Email Service Configuration (Gmail)
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-16-character-gmail-app-password

# CORS Configuration
FRONTEND_URL=http://localhost:5173
```

### Setting Up Required Services

#### MongoDB Atlas
1. Create a free account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster
3. Add your IP address to the whitelist
4. Create a database user
5. Get your connection string and add it to `MONGO_URI`

#### Google OAuth
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Google+ API
4. Create OAuth 2.0 credentials
5. Add authorized redirect URIs
6. Copy Client ID and Client Secret to your `.env` file

#### Gmail App Password
1. Enable 2-Factor Authentication on your Gmail account
2. Go to Google Account settings
3. Generate an App Password for "Mail"
4. Use the 16-character password in `EMAIL_PASS`

## 📁 Project Structure

```
note-taking-app/
├── note-app-server/          # Backend API
│   ├── src/
│   │   ├── controllers/      # Request handlers
│   │   ├── middleware/       # Authentication & validation
│   │   ├── models/          # Database schemas
│   │   ├── routes/          # API endpoints
│   │   ├── utils/           # Helper functions
│   │   └── server.ts        # Server entry point
│   ├── .env                 # Environment variables
│   └── package.json
├── note-app-client/         # Frontend React app
│   ├── src/
│   │   ├── components/      # Reusable components
│   │   ├── pages/          # Page components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── utils/          # Helper functions
│   │   └── App.tsx         # Main app component
│   └── package.json
└── README.md
```

## 🔗 API Endpoints

### Authentication
- `POST /api/auth/signup` - Register new user with email
- `POST /api/auth/verify-otp` - Verify OTP and complete registration
- `POST /api/auth/signin` - Sign in with email (sends OTP)
- `POST /api/auth/google` - Google OAuth authentication

### Notes Management
- `GET /api/notes` - Get all user notes
- `POST /api/notes` - Create a new note
- `DELETE /api/notes/:id` - Delete a specific note

## 🚦 Usage

1. **Registration**: New users can sign up using their email address
2. **Email Verification**: Check your email for the OTP and verify your account
3. **Sign In**: Use your email to receive a new OTP for signing in
4. **Google Auth**: Alternatively, use "Sign in with Google" for instant access
5. **Create Notes**: Once authenticated, start creating and managing your notes
6. **Security**: Your session remains secure with JWT tokens

## Troubleshooting

### Common Issues

**MongoDB Connection Failed**
- Verify your connection string in the `.env` file
- Check if your IP address is whitelisted in MongoDB Atlas
- Ensure your database user has the correct permissions

**Email OTP Not Received**
- Check your spam/junk folder
- Verify your Gmail App Password is correct
- Ensure 2-Factor Authentication is enabled on your Gmail account

**Google OAuth Not Working**
- Verify your Google Client ID and Secret
- Check that your redirect URIs are properly configured
- Ensure the Google+ API is enabled in your Google Cloud project



---