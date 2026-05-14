# Genie - Master Project Documentation & Source Map

This document consolidates the General Overview, Technical Specifications, and SDLC Report for the "Genie - AI Website Builder" project. Use this file as a comprehensive context for AI analysis.

---

## 1. Project Overview (README Context)
Genie is a MERN-stack platform that uses Large Language Models (LLMs) to generate production-grade websites from text prompts.

### Key Features
- **AI Generation**: Powered by DeepSeek via OpenRouter.
- **Credit System**: Consumption-based model (50/25 credits).
- **Live Preview**: Real-time iframe rendering.
- **Editing**: Integrated Monaco Editor.
- **Billing**: Stripe payment integration.

---

## 2. SDLC Implementation Model

### Phase 1: Planning
- **Goal**: Automate frontend development for non-technical users.
- **Feasibility**: High, using existing LLM capabilities for code generation.

### Phase 2: Requirements (SRS)
- **Functional**: Google Auth, AI Prompting, Real-time Editing, Deploy/Slug generation, Stripe Payments.
- **Non-Functional**: Responsiveness (Tailwind 4), Security (JWT/HttpOnly), Low Latency.

### Phase 3: System Design
- **Architecture**: MERN (MongoDB, Express, React, Node).
- **Data Model**:
  - `User`: Credits, Plan, OAuth details.
  - `Website`: Code, Conversation History, Deployment URL/Slug.

### Phase 4: Implementation (Source Code Modules)
- **Backend Controller (`website.controllers.js`)**: Handles the complex logic of prompt construction and credit deduction.
- **Frontend Editor (`WebsiteEditor.jsx`)**: Uses `srcDoc` and `Blob URLs` for instant code preview.
- **Auth Middleware (`isAuth.js`)**: Ensures stateless security via JWT verification.

### Phase 5: Testing
- Manual testing of AI JSON parsing.
- Integration testing of Stripe Webhooks for credit fulfillment.

### Phase 6: Deployment
- **Infrastructure**: Vercel (Frontend/Backend), MongoDB Atlas.

---

## 3. Technical Specifications

### API Reference Table
| Route | Description |
| :--- | :--- |
| `POST /api/auth/google` | OAuth exchange and session creation. |
| `POST /api/website/generate`| AI generation (Master Prompt execution). |
| `POST /api/website/update` | Iterative code refinement. |
| `GET /api/website/deploy` | Slug creation and visibility toggle. |
| `POST /api/billing` | Stripe Checkout session creation. |

### Data Schema (Mongoose)
```javascript
const websiteSchema = {
  user: ObjectId,
  title: String,
  latestCode: String,
  conversation: [{ role: String, content: String }],
  deployed: Boolean,
  slug: String
};
```

---

## 4. Critical Logic: The Master Prompt
The system's core intelligence relies on a "Principal Frontend Architect" prompt that enforces:
- **Single-File Output**: All HTML, CSS, and JS in one document for easy previewing.
- **No External Dependencies**: Prevents broken styles or scripts.
- **Responsive Grid**: Mandatory use of CSS Flex/Grid.
- **Business Logic**: No "Lorem Ipsum"; AI must generate real copy.

---

## 5. Maintenance & Future Roadmap
1. **Multi-file Exports**: Move from single HTML to React/Vite project exports.
2. **Domain Mapping**: Allow custom DNS settings.
3. **Advanced AI Models**: Integration with GPT-4o or Claude 3.5 Sonnet for even higher fidelity.
