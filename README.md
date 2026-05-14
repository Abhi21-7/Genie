# 🧞 Genie.ai - The Ultimate AI Website Builder

![Genie.ai Banner](https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1200&q=80)

## 🌟 Overview

**Genie.ai** is a sophisticated, full-stack MERN application that leverages cutting-edge Generative AI to transform natural language prompts into high-end, responsive, and production-ready websites. Designed for the 2026-2027 design era, Genie eliminates the technical barriers to web development, allowing anyone to create stunning digital experiences in seconds.

---

## 📑 Table of Contents

1.  [🚀 Key Features](#-key-features)
2.  [💻 Technology Stack](#-technology-stack)
3.  [🏗️ System Architecture](#️-system-architecture)
4.  [📂 Directory Structure](#-directory-structure)
5.  [⚙️ Installation & Setup](#️-installation--setup)
6.  [🔑 Environment Variables](#-environment-variables)
7.  [📡 API Documentation](#-api-documentation)
8.  [🤖 AI Prompting Strategy](#-ai-prompting-strategy)
9.  [💳 Credit & Billing System](#-credit--billing-system)
10. [🔒 Security & Authentication](#-security--authentication)
11. [🎨 Frontend Design System](#-frontend-design-system)
12. [🗄️ Database Schema](#️-database-schema)
13. [🚀 Deployment Guide](#-deployment-guide)
14. [📈 SDLC Report](#-sdlc-report)
15. [🔮 Future Roadmap](#-future-roadmap)
16. [🤝 Contributing](#-contributing)
17. [📜 License](#-license)

---

## 🚀 Key Features

### 1. Instant AI Generation
Describe your website in plain English (e.g., "A dark-themed portfolio for a creative photographer with a gallery and contact form"), and Genie will generate the full HTML, CSS, and JS.

### 2. Live Preview Environment
Watch your website come to life in a real-time, responsive `iframe` preview. Toggle between mobile, tablet, and desktop views to ensure perfect responsiveness.

### 3. Iterative AI Editing
Not happy with a specific section? Tell the AI to "Change the primary color to emerald green" or "Add a testimonial section," and the code updates instantly.

### 4. Integrated Monaco Editor
For developers, Genie includes a built-in Monaco Editor (the engine behind VS Code) for manual fine-tuning and code exploration.

### 5. Credit-Based Economy
A robust monetization system where users consume credits for generation and updates. Integrated with **Stripe** for seamless top-ups.

### 6. One-Click Deployment
Deploy your generated websites to a public URL instantly. Genie generates SEO-friendly slugs for easy sharing.

---

## 💻 Technology Stack

### Frontend
- **React 19**: Utilizing the latest React features for optimal performance.
- **Tailwind CSS 4**: Next-gen styling with the `@tailwindcss/vite` plugin.
- **Framer Motion**: Premium micro-animations and transitions.
- **Redux Toolkit**: Centralized state management for user data and credits.
- **Lucide React**: Clean, consistent iconography.
- **Vite**: Ultra-fast build tool and development server.

### Backend
- **Node.js & Express.js**: Scalable RESTful API architecture.
- **MongoDB Atlas**: Cloud-hosted NoSQL database for users and websites.
- **Firebase Admin SDK**: Secure Google OAuth token verification.
- **OpenRouter (DeepSeek LLM)**: State-of-the-art AI generation engine.
- **Stripe SDK**: Secure payment processing and webhook handling.

### DevOps
- **Vercel**: Unified hosting for frontend and serverless backend.
- **Git/GitHub**: Version control and CI/CD.

---

## 🏗️ System Architecture

Genie.ai follows a **Decoupled Layered Architecture**:

1.  **Presentation Layer (Frontend)**: React SPA handles user interaction, code rendering, and state management.
2.  **Logic Layer (Backend)**: Express controllers manage AI orchestration, credit deduction, and business logic.
3.  **Data Layer (MongoDB)**: Persists user profiles, website code, and conversation history.
4.  **Intelligence Layer (OpenRouter)**: External LLMs process prompts and generate code.
5.  **Payment Layer (Stripe)**: Handles financial transactions and fulfillment.

---

## 📂 Directory Structure

### Root Directory
- `client/`: The React-based frontend application.
- `server/`: The Express-based backend application.
- `api/`: Vercel serverless functions entry point (`index.js`).
- `vercel.json`: Configuration for Vercel deployment and routing.
- `package.json`: Project metadata and shared dev dependencies.
- `README.md`: The document you are currently reading.

### Client Deep Dive (`/client`)
- **`src/main.jsx`**: Entry point for the React application.
- **`src/App.jsx`**: Main router and global provider wrapper.
- **`src/pages/`**:
  - `Home.jsx`: Landing page with feature highlights and call-to-action.
  - `Dashboard.jsx`: User workspace for managing projects.
  - `Generate.jsx`: Prompt-to-website interface with progress tracking.
  - `Editor.jsx`: Integrated Monaco Editor + Live Preview environment.
  - `Pricing.jsx`: Credit top-up plans and Stripe integration UI.
  - `LiveSite.jsx`: Public viewing route for deployed sites.
- **`src/components/`**:
  - `LoginModal.jsx`: Firebase Google Auth integration.
- **`src/redux/`**:
  - `userSlice.js`: Redux state for user profile and credits.
  - `store.js`: Global state configuration.
- **`src/hooks/`**:
  - `useGetCurrentUser.js`: Hook to fetch and sync user data on refresh.
- **`vite.config.js`**: Vite and Tailwind 4 configuration.

### Server Deep Dive (`/server`)
- **`index.js`**: Main entry point, middleware setup, and route mounting.
- **`config/`**:
  - `db.js`: MongoDB connection logic using Mongoose.
  - `openRouter.js`: AI API client configuration.
  - `stripe.js`: Stripe SDK initialization.
  - `firebase.js`: Firebase Admin SDK for token verification.
- **`controllers/`**:
  - `auth.controller.js`: Google login and JWT generation.
  - `website.controllers.js`: AI generation, update logic, and deployment.
  - `user.controllers.js`: User profile and credit fetching.
  - `billing.controller.js`: Stripe checkout session creation.
  - `stripeWebhook.controller.js`: Payment fulfillment and credit adding.
- **`models/`**:
  - `user.model.js`: User schema (email, credits, plan).
  - `website.model.js`: Website schema (code, prompt history, slug).
- **`routes/`**: Route definitions for all modules.
- **`middlewares/`**:
  - `isAuth.js`: JWT verification and route protection.
- **`utils/`**:
  - `extractJson.js`: Utility to parse JSON from AI's markdown responses.

---

## ⚙️ Installation & Setup

### Prerequisites
- Node.js (v18+)
- MongoDB Atlas Account
- Firebase Project
- OpenRouter API Key
- Stripe Account

### 1. Clone the Repository
```bash
git clone https://github.com/Jatinsingh1808/Interview-Agent.git
cd Interview-Agent
```

### 2. Backend Setup
```bash
cd server
npm install
```
Create a `.env` file in the `server` directory (see [Environment Variables](#-environment-variables)).

### 3. Frontend Setup
```bash
cd ../client
npm install
```
Create a `.env` file in the `client` directory.

### 4. Run Locally
**Start Backend:**
```bash
cd server
npm run dev
```

**Start Frontend:**
```bash
cd client
npm run dev
```

---

## 🔑 Environment Variables

### Server (`server/.env`)
| Key | Description |
| :--- | :--- |
| `PORT` | Backend port (default 8000) |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret for session tokens |
| `OPENROUTER_API_KEY` | API key from OpenRouter |
| `STRIPE_SECRET_KEY` | Stripe secret key |
| `STRIPE_WEBHOOK_SECRET`| Stripe webhook signing secret |
| `FIREBASE_PROJECT_ID` | Firebase project ID |
| `FIREBASE_CLIENT_EMAIL`| Firebase service account email |
| `FIREBASE_PRIVATE_KEY` | Firebase service account private key |
| `FRONTEND_URL` | URL of the frontend (for CORS) |

### Client (`client/.env`)
| Key | Description |
| :--- | :--- |
| `VITE_SERVER_URL` | Backend API URL |
| `VITE_FIREBASE_API_KEY`| Firebase client API key |
| `VITE_STRIPE_PUBLIC_KEY`| Stripe publishable key |

---

## 📡 API Documentation

### Authentication
- `POST /api/auth/google`: Login/Signup with Google ID Token.
- `GET /api/auth/logout`: Clear session cookies.

### User
- `GET /api/user/me`: Get current user profile and credits.

### Website Management
- `POST /api/website/generate`: Create a new website (**Cost: 50 Credits**).
- `POST /api/website/update/:id`: Update existing code via AI (**Cost: 25 Credits**).
- `GET /api/website/get-all`: List all user websites.
- `GET /api/website/get-by-id/:id`: Fetch specific website details.
- `GET /api/website/deploy/:id`: Generate public slug and deploy.
- `GET /api/website/get-by-slug/:slug`: Public route for live sites.

### Billing
- `POST /api/billing`: Create Stripe Checkout session.
- `POST /api/stripe/webhook`: Fulfillment listener (credits top-up).

---

## 🤖 AI Prompting Strategy

Genie uses a **Master Prompt Architecture** to ensure the AI behaves as a "Principal Frontend Architect". 

### Constraints enforced:
- **Single File Output**: All HTML, CSS, and JS in one file for `srcdoc` compatibility.
- **Responsive by Default**: Mobile-first approach using CSS Grid/Flexbox.
- **Asset Handling**: Dynamic image fetching from Unsplash with optimized parameters.
- **SPA Logic**: Vanilla JS used for page transitions within the generated site.
- **Strict JSON**: AI must return a valid JSON object: `{ "message": "...", "code": "..." }`.

---

## 💳 Credit & Billing System

Genie operates on a "Pay-as-you-go" credit model:
- **New User Bonus**: 100 Free Credits.
- **Generation**: 50 Credits.
- **AI Update**: 25 Credits.

**Stripe Integration:**
1.  User selects a plan (Starter, Pro, etc.).
2.  Server creates a `stripe.checkout.sessions`.
3.  User pays on Stripe's secure page.
4.  Stripe sends a `checkout.session.completed` event to Genie's webhook.
5.  Server validates the signature and adds credits to the user's MongoDB record.

---

## 🔒 Security & Authentication

- **Google OAuth**: Handled by Firebase on the client, verified on the server.
- **JWT Session Management**: Sessions are managed via **HttpOnly, Secure, SameSite:Strict** cookies to prevent XSS and CSRF.
- **Credit Validation**: Credit checks happen on the server-side before any AI request is sent.
- **Iframe Sandboxing**: Generated code is rendered in a sandboxed `iframe` using `srcdoc` to isolate it from the main application.

---

## 🎨 Frontend Design System

- **Theme**: Dark Mode (Modern Stealth).
- **Typography**: System Inter-stack for performance and clarity.
- **Colors**:
  - Background: `#040404`
  - Accent: Purple-to-Blue Linear Gradient
  - Cards: `white/5` with `backdrop-blur`
- **Animations**: Subtle entrance animations using `framer-motion`.

---

## 🚀 Deployment Guide

### Vercel Configuration
Genie.ai is optimized for Vercel using `vercel.json`:
```json
{
  "rewrites": [
    { "source": "/api/(.*)", "destination": "/api/index.js" },
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```
The `api/index.js` file bridges the Express app to Vercel's serverless environment.

### Production Steps
1.  Connect GitHub repo to Vercel.
2.  Set Environment Variables in Vercel Dashboard.
3.  Configure MongoDB Atlas Network Access (Allow all IPs or Vercel IPs).
4.  Set Stripe Webhook URL to `https://your-domain.com/api/stripe/webhook`.

---

## 📈 SDLC Report

### Phase 1: Requirement Analysis
Identified the need for an AI-powered tool that produces real code, not just mockups. Defined the MERN stack as the core technology.

### Phase 2: Design
Designed a credit-based system and a master prompt that guarantees high-quality, responsive output.

### Phase 3: Implementation
Built the backend logic for AI orchestration and the frontend for live code preview and editing.

### Phase 4: Testing
Conducted unit tests for JSON extraction and integration tests for the Stripe-to-Credits flow.

### Phase 5: Deployment
Launched on Vercel with a serverless Express backend.

---

## 🔮 Future Roadmap

- [ ] **Multi-File Projects**: Support for React/Next.js output.
- [ ] **Custom Domains**: Allow users to point their own domains to Genie-hosted sites.
- [ ] **Image Generation**: Integrate DALL-E 3 for custom branding assets.
- [ ] **Asset Manager**: A dashboard for users to upload and manage their own images/logos.
- [ ] **Collaboration**: Shared workspaces for teams.

---

## 🤝 Contributing

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---

