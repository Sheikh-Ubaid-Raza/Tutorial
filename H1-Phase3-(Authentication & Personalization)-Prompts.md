
---

### 1. Updated Specification Prompt (`/spec`)

```markdown
/spec
**OBJECTIVE:**
Define the architecture for **Phase 3: User Authentication, Content Personalization, and Urdu Translation**.

**CURRENT STATUS (DO NOT MODIFY):**
* **Phase 1 (Frontend):** Docusaurus Textbook is successfully deployed and content is written.
* **Phase 2 (Backend):** RAG Chatbot (FastAPI + Vector DB) is fully functional and tested.
* **CONSTRAINT:** Do NOT refactor, touch, or modify the existing Docusaurus content structure or the RAG Chatbot logic. Focus ONLY on adding the *new* layer for Auth, Personalization, and Translation.

**CONTEXT:**
We are adding a "Hybrid Microservice" layer to our existing project:
1.  **Auth Service (NEW):** A lightweight Node.js/Hono service using `better-auth`.
2.  **AI Service (EXISTING):** The Python FastAPI backend (will be extended).
3.  **Database:** Shared Neon Postgres.

**REQUIREMENT 1: Authentication & Data Collection (Node.js)**
* **Tool:** Use `better-auth` (TypeScript).
* **Schema Extension:** The `user` table MUST store:
    * `software_background` (Enum: "Beginner", "Intermediate", "Advanced")
    * `hardware_background` (Enum: "None", "Arduino", "RaspberryPi")
    * `learning_goal` (Text)
* **UX:** On "Sign Up", prompt the user to fill these fields.
* **Integration:** Ensure the Auth Token is accessible to the Docusaurus frontend.

**REQUIREMENT 2: Personalization Engine (Python)**
* **Trigger:** A "✨ Personalize Chapter" button on the Docusaurus Frontend.
* **Flow:**
    1.  Frontend sends `chapter_content` + `user_id` to Python Backend.
    2.  Python Backend fetches user's `software_background` from the Shared DB.
    3.  **AI Processing:**
        * **Provider:** OpenRouter.
        * **Model:** `meta-llama/llama-3.1-70b-instruct` or `qwen/qwen-2.5-72b-instruct`.
        * **Prompt:** "Rewrite this content for a user who is a [Level] in software..."

**REQUIREMENT 3: Urdu Translation Engine (Bonus Feature)**
* **Objective:** Allow logged-in users to read the chapter in Urdu.
* **Trigger:** A "🌐 Translate to Urdu" button at the start of each chapter (next to Personalize).
* **Constraint:** **Strictly for Logged-in Users only.** If not logged in, show Auth Modal.
* **AI Processing:**
    * **Endpoint:** `POST /api/translate`
    * **Model:** Use `qwen/qwen-2.5-72b-instruct` (Excellent for Urdu/English mix).
    * **Prompting Strategy:** Do not just translate word-for-word. Maintain technical terms (like 'ROS 2', 'Node', 'Latency') in English but explain the concept in natural Urdu (Roman Urdu or Script depending on configuration, default to Urdu Script).
    * **Performance:** Stream the response to handle long chapters gracefully.

**OUTPUT:**
* Define the Shared Database Schema (SQL).
* Define the API Contract for the new Node Auth Service.
* Define the API Contracts for BOTH Python Endpoints (Personalization & Translation).

```

---

### 2. Updated Implementation Plan (`/plan`)

```markdown
/plan
**ACTION REQUIRED:**
Generate the Implementation Roadmap for **Phase 3 (Auth + Personalization + Translation)**.

**STRATEGY:**
Execute strictly in order: **Data Collection (Auth)** first, then **AI Features (Personalization & Translation)**.

**Sub-Phase 3.1: SCAFFOLD Auth Service (Node.js)**
1.  **Create** `/auth-service` directory (outside `/backend`).
2.  **Initialize** Node.js project with `hono`, `better-auth`, `pg`, `dotenv`.
3.  **Database:** Connect to the **existing Neon Postgres** (Share `DATABASE_URL` from Phase 2).
4.  **Schema Migration:** Apply schema updates (User table + Background fields).

**Sub-Phase 3.2: INTEGRATE Frontend Auth**
5.  **Install** `@better-auth/react` in Docusaurus.
6.  **Build** `AuthModal.tsx`:
    * **Sign In:** Standard Email/Pass.
    * **Sign Up:** Email/Pass + **Select Inputs** for Software/Hardware background.
7.  **Verification:** Test User Signup and verify data in Neon DB.

**Sub-Phase 3.3: BUILD AI Backend Endpoints (Python)**
8.  **Update** Python Requirements: Ensure async DB drivers (`asyncpg`) are ready.
9.  **Implement** `POST /api/personalize`:
    * Fetch `software_background` -> Call OpenRouter (Personalization Prompt).
10. **Implement** `POST /api/translate` (Urdu Feature):
    * **Input:** Chapter Text + User Token (to verify login).
    * **Logic:** Call OpenRouter (Qwen-2.5-72B) with system prompt: *"You are an expert technical translator. Translate the following technical documentation into professional Urdu. Keep key technical terms (e.g., Docker, API, Latency) in English."*
    * **Streaming:** Implement Server-Sent Events (SSE) or chunked streaming for fast UI feedback.

**Sub-Phase 3.4: FRONTEND "Smart Toolbar"**
11. **Swizzle** Docusaurus `DocItem` layout to inject a **Toolbar Component** at the top.
12. **UI Implementation:**
    * Add two buttons: "✨ Personalize" and "🌐 Urdu Translation".
    * **Logic:** Clicking either button checks `session`.
        * If `!session` -> Open `AuthModal`.
        * If `session` -> Call respective API (`/personalize` or `/translate`).
13. **Display Logic:**
    * Show a loading skeleton while streaming.
    * Replace the original English text with the received AI response dynamically.
    * Add a "Revert to Original" button to switch back.


```
