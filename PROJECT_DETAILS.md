# Genie - Technical Project Specification

This document provides a deep dive into the technical implementation of Genie, an AI-powered website builder. It is designed to be consumed by developers or AI agents for project analysis and expansion.

---

## 🏗️ System Architecture

Genie follows a decoupled client-server architecture:
- **Frontend**: Single Page Application (SPA) built with React and Vite.
- **Backend**: RESTful API built with Express.js and Node.js.
- **Database**: NoSQL storage using MongoDB Atlas.
- **AI Engine**: LLM orchestration via OpenRouter (DeepSeek model).

---

## 🛠️ API Reference

| Endpoint | Method | Auth | Description |
| :--- | :--- | :--- | :--- |
| `/api/auth/google` | POST | No | Authenticates user via Google OAuth (Firebase token exchange). |
| `/api/auth/logout` | GET | Yes | Clears authentication cookies. |
| `/api/user/me` | GET | Yes | Retrieves current user profile and credit balance. |
| `/api/website/generate` | POST | Yes | Generates a new website. Costs **50 credits**. |
| `/api/website/update/:id`| POST | Yes | Updates existing code via AI. Costs **25 credits**. |
| `/api/website/get-all` | GET | Yes | Fetches all websites owned by the user. |
| `/api/website/get-by-id/:id`| GET | Yes | Fetches specific website data and conversation history. |
| `/api/website/deploy/:id` | GET | Yes | Toggles deployment status and generates a public slug. |
| `/api/website/get-by-slug/:slug`| GET | No | Public endpoint to fetch website code for live viewing. |
| `/api/billing` | POST | Yes | Initiates Stripe Checkout session for credit top-ups. |
| `/api/stripe/webhook` | POST | No | Handles Stripe events (payment success) to add credits. |

---

## 📊 Data Models (Mongoose)

### User Model
```javascript
{
  name: String,
  email: { type: String, unique: true },
  avatar: String,
  credits: { type: Number, default: 100 },
  plan: { type: String, enum: ["free", "pro", "enterprise"], default: "free" }
}
```

### Website Model
```javascript
{
  user: ObjectId (ref: "User"),
  title: String,
  latestCode: String,
  conversation: [
    { role: String, content: String, timestamp: Date }
  ],
  deployed: Boolean,
  deployUrl: String,
  slug: { type: String, unique: true }
}
```

---

## 🤖 AI Prompting Strategy

The system uses a **Master Prompt** to ensure high-quality output. The AI is instructed to behave as a "Principal Frontend Architect".

**Key constraints enforced:**
- Output must be a **single valid HTML document**.
- Style and Script must be internal (no external files except Unsplash images).
- Must use **CSS Grid/Flexbox** for responsiveness.
- Must implement **SPA-style navigation** using vanilla JavaScript.
- **Strict JSON response format**: `{ "message": "...", "code": "..." }`.

---

## 🔒 Authentication & Security

1. **Client-side**: Firebase Auth handles the Google Sign-in popup and returns an ID token.
2. **Server-side**: 
   - The token is verified.
   - A custom JWT is generated and stored in an **HttpOnly cookie**.
   - `isAuth` middleware protects private routes by verifying the JWT.
3. **CORS**: Configured to allow requests only from the specified `FRONTEND_URL` with `credentials: true`.

---

## 💳 Credit & Billing Logic

- **Initialization**: New users get 100 free credits.
- **Consumption**:
  - `generateWebsite`: -50 credits.
  - `updateWebsite`: -25 credits.
- **Top-up**: 
  - Integrated with **Stripe Checkout**.
  - Webhook listener updates the user's `credits` and `plan` fields upon successful payment.

---

## 🖥️ Frontend Implementation Details

- **Routing**: `react-router-dom` (v7) manages paths:
  - `/`: Landing page.
  - `/dashboard`: User's project list.
  - `/generate`: Prompt input and generation UI.
  - `/editor/:id`: Monaco Editor view with live preview (iframe).
  - `/site/:slug`: Public viewing route.
- **Styling**: Tailwind CSS 4 with the `@tailwindcss/vite` plugin.
- **Animations**: `framer-motion` for smooth modal transitions and loading states.
- **Preview**: The generated code is rendered in an `<iframe>` using the `srcdoc` attribute for security and isolation.

---

## 🚀 Deployment (Vercel)

The `vercel.json` and `api/index.js` configuration allows the Express app to run as a single serverless function. 
- **Root Directory**: Project root.
- **Backend Entry**: `api/index.js` -> `server/index.js`.
- **Frontend Build**: Vite build output.
