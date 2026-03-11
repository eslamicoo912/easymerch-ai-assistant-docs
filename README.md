# EASYMERCH.AI - GPT Assistant Lab 🚀

A high-performance, full-stack AI platform designed to unify advanced text generation, image manipulation, and smart productivity tools into a single, intuitive interface.

## 🌟 Overview

**GPT Assistant Lab** is a professional-grade AI workspace built for developers, designers, and power users who need a centralized hub for state-of-the-art AI capabilities. Unlike fragmented solutions, this project integrates multiple leading AI models (OpenAI, Stability AI, etc.) into a cohesive ecosystem. It solves the problem of "tab-fatigue" and complex API management by providing a streamlined, secure, and usage-monitored environment for all generative AI needs.

## ✨ Features

- **🧠 Multi-Model AI Chat**: Seamless interaction with specialized GPT models for keyword extraction, idea generation, and creative prompting.
- **🎨 Image Studio**: 
  - Text-to-Image generation using DALL-E 3 and Stability AI.
  - Image-to-Image transformations and variations.
  - AI-powered background removal and vector conversion.
- **🔐 Secure User Ecosystem**: Robust authentication with OTP verification and JWT-protected sessions.
- **💳 Subscription & Usage Management**: Tiered subscription plans (integrated with Stripe) and real-time usage tracking for GPT and image requests.


## 🏗️ Architecture & Technical Decisions

### System Design Overview
The project follows a **decoupled Client-Server architecture** using the MERN stack (MongoDB, Express, React, Node) enhanced with **TypeScript** on the backend for type safety and scalability.

### Key Technical Decisions
- **TypeScript Integration**: Implemented in the backend to ensure rigorous data validation and reduce runtime errors in complex AI logic.
- **Centralized API Router**: Designed a scalable routing system in `index.router.ts` to manage versioning (`/api/v1`) and global error handling as middleware.
- **Tiered Request Limiting**: Built a custom usage tracking system within `chat.controllers.ts` that cross-references user plans before executing heavy AI operations.

## 🛠️ Tech Stack

**Frontend:**
- React.js (Hooks & Context API)
- Tailwind CSS
- Material UI (MUI)
- Formik & Yup (Form Management)
- Axios (HTTP Client)

**Backend:**
- Node.js & Express
- TypeScript
- MongoDB & Mongoose
- OpenAI API (GPT-4/3.5, DALL-E)
- Google Cloud Vision & Stability AI
- Stripe (Payment Gateway)
- Cloudinary (Media Hosting)

## ⚡ Challenges & How I Solved Them

| Challenge | Solution |
| :--- | :--- |
| **API Rate Limits** | Implemented a plan-based usage counter in the database, checking quotas *before* calling expensive external AI services. |
| **Asynchronous UI States** | Leveraged React Hot Toast and custom hooks to provide real-time feedback during long-running AI generation processes. |
| **Data Integrity** | Utilized **Joi** for comprehensive request validation on every endpoint to prevent malformed data from hitting the database or AI APIs. |

## 📊 Data Model (High Level)

The system relies on a relational-like schema within MongoDB:
- **User**: Stores profiles, encrypted credentials, and current plan status.
- **Chat**: Maintains context-aware history linked to specific AI models and users.
- **Plan**: Defines quotas for different request types (GPT, Image, Vectorization).
- **GPTModel**: Configuration and settings for various integrated AI engines.

## 🔌 API Overview

### 👤 User Module
- `POST /api/v1/user/signup`: Secure registration with Joi validation.
- `POST /api/v1/user/login`: User authentication and JWT issuance.
- `PATCH /api/v1/user/generate-otp`: Request OTP for verification or password reset.
- `PUT /api/v1/user/confirm-email`: Finalize account activation via OTP.
- `PATCH /api/v1/user/reset-password/:token`: Secure password recovery flow.
- `GET /api/v1/user/`: Fetch authenticated user profile.
- `PATCH /api/v1/user/`: Logout and session termination.

### 💳 Plans & Subscriptions
- `GET /api/v1/plans`: Retrieve all available subscription tiers.
- `PUT /api/v1/plans/subscribe/:_id`: Initiate a plan subscription (Stripe integration).
- `PUT /api/v1/plans/confirm/:token`: Confirm successful payment and activate plan.
- `PUT /api/v1/plans/cancel/:token`: Handle payment cancellation or failures.

### 💬 AI & Chat Services
- `POST /api/v1/chat/generate`: Unified endpoint for multi-model AI completions.
- `GET /api/v1/chat/:model`: Retrieve chat history for specific AI models.
- `DELETE /api/v1/chat/:model`: Clear chat context for a specific model.

## 🛡️ Security Considerations

- **JWT Authentication**: Secure session management using JSON Web Tokens.
- **OTP Verification**: Multi-factor authentication during signup and password recovery.
- **Input Sanitization**: All incoming data is validated using **Joi/Zod** schemas to prevent injection attacks.
- **Secure Environment**: Secrets and API keys are strictly managed via environment variables (never committed to VCS).
- **CORS & Middleware**: Configured for restricted origins with global error handling to prevent sensitive data leakage.

## 📖 What I Learned

Building this project deepened my expertise in **orchestrating multiple third-party AI APIs** into a single application. I mastered the art of building **usage-aware backend systems** and gained significant experience in managing **complex state transitions** in React during high-latency AI operations. It reinforced the importance of **TypeScript** for long-term codebase maintainability.

---
*Created by :*

**Eslam Ashraf**  
Backend-focused MERN Developer

- 🌐 [Portfolio](https://eslamicoo912.github.io)
- 💼 [LinkedIn](https://linkedin.com/in/your-profile](https://www.linkedin.com/in/eslamicoo912/))
- 🐙 [GitHub](https://github.com/your-username](https://github.com/eslamicoo912))
- 📧 eslamicoo3@gmail.com

---

> 💡 *This repository is private as "easymerch" is a commercial product under active development.  
> For a walkthrough of the codebase or architecture, feel free to reach out directly.*
