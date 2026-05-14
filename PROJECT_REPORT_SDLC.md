# Comprehensive Project Report: Genie - AI Website Builder

**Document Type**: SDLC Project Documentation  
**Developer**: Abhishek Agnihotri  
**Project Name**: Genie  
**Domain**: Artificial Intelligence & Full-Stack Web Development  

---

## 📋 Table of Contents
1. [Introduction](#1-introduction)
2. [SDLC Phase 1: Planning & Requirement Analysis](#2-sdlc-phase-1-planning--requirement-analysis)
3. [SDLC Phase 2: Defining Requirements (SRS)](#3-sdlc-phase-2-defining-requirements-srs)
4. [SDLC Phase 3: System Design](#4-sdlc-phase-3-system-design)
5. [SDLC Phase 4: Implementation & Coding](#5-sdlc-phase-4-implementation--coding)
6. [SDLC Phase 5: Testing](#6-sdlc-phase-5-testing)
7. [SDLC Phase 6: Deployment & Maintenance](#7-sdlc-phase-6-deployment--maintenance)
8. [Conclusion & Future Scope](#8-conclusion--future-scope)

---

## 1. Introduction
Genie is a next-generation AI-powered platform that democratizes website creation. By utilizing Large Language Models (LLMs), it allows users to describe their business or personal needs in plain English and receive a fully functional, responsive website in seconds.

---

## 2. SDLC Phase 1: Planning & Requirement Analysis

### 2.1 Objectives
- To eliminate the technical barrier to website creation.
- To provide a high-quality, mobile-first design system automatically.
- To create a sustainable business model using a credit-based subscription.

### 2.2 Scope
- **AI Generation**: Custom HTML/CSS/JS generation.
- **Editing**: Real-time code refinement via AI or manual editor.
- **Hosting**: Instant "deployment" via unique public slugs.

### 2.3 Feasibility Study
- **Technical**: Leverages stable MERN stack and high-performance LLMs (DeepSeek).
- **Economic**: Low overhead using serverless architecture and API-on-demand pricing.

---

## 3. SDLC Phase 2: Defining Requirements (SRS)

### 3.1 Functional Requirements
- **FR1: Authentication**: Users must login via Google OAuth.
- **FR2: Website Generation**: System must generate a website based on a prompt (Cost: 50 credits).
- **FR3: AI Updates**: System must update existing code based on iterative prompts (Cost: 25 credits).
- **FR4: Preview**: Users must see a live rendering of the code in an iframe.
- **FR5: Billing**: Users must be able to purchase credits via Stripe.

### 3.2 Non-Functional Requirements
- **Performance**: AI response should be parsed and displayed within 15-30 seconds.
- **Security**: User data and tokens must be stored in encrypted/HttpOnly formats.
- **Scalability**: Backend should handle multiple concurrent AI requests using serverless scaling.

---

## 4. SDLC Phase 3: System Design

### 4.1 System Architecture (MERN Stack)
- **Frontend**: React 19 + Tailwind 4 (Presentation Layer).
- **Backend**: Node.js + Express (Application Layer).
- **Database**: MongoDB (Data Layer).
- **AI Integration**: OpenRouter API (Intelligence Layer).

### 4.2 Database Design (Schema Level)
- **User Schema**: Stores profile, credit balance, and subscription plan.
- **Website Schema**: Stores generated code, conversation history (context), and deployment status.

### 4.3 UI/UX Design Principles
- **Minimalism**: Clean, dark-themed dashboard.
- **Instant Feedback**: Progress bars and loading states during AI generation.
- **Developer-Friendly**: Integrated Monaco Editor for advanced users.

---

## 5. SDLC Phase 4: Implementation & Coding

### 5.1 Tech Stack Breakdown
- **Language**: JavaScript (ES6+).
- **UI**: React 19, Lucide Icons, Framer Motion.
- **State**: Redux Toolkit (User context management).
- **Backend**: Express.js with custom `isAuth` middleware.
- **AI**: DeepSeek-Chat model via OpenRouter.

### 5.2 Module Description
- **Auth Module**: Handles Firebase token verification and JWT session management.
- **Generation Module**: Constructs complex "Master Prompts" to guide the AI.
- **Billing Module**: Handles Stripe Checkout sessions and secure Webhook fulfillment.
- **Editor Module**: Syncs code between the AI output, the Monaco Editor, and the Live Preview iframe.

---

## 6. SDLC Phase 5: Testing

### 6.1 Unit Testing
- Verification of utility functions like `extractJson.js` to ensure AI responses are correctly formatted.
- Verification of credit deduction logic in `website.controllers.js`.

### 6.2 Integration Testing
- Testing the flow from **Login -> Prompt -> Generation -> Credits Updated**.
- Testing Stripe Webhooks using the Stripe CLI to ensure credits are added post-payment.

---

## 7. SDLC Phase 6: Deployment & Maintenance

### 7.1 Deployment Strategy
- **Platform**: Vercel (Frontend & Serverless Backend).
- **Database**: MongoDB Atlas (Cloud Cluster).
- **Environment Management**: Secure secrets stored in Vercel/Local `.env` files.

---

## 8. Conclusion & Future Scope
Genie successfully demonstrates the power of generative AI in web development. 

**Future Enhancements include:**
- Support for multi-file projects (React/Next.js output).
- Domain mapping for users to connect their own URLs.
- Image generation (DALL-E/Midjourney) integration to replace Unsplash stock photos.
- SEO optimization tools for generated websites.
