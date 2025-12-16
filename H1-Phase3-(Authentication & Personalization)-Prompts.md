Here are the **Final, Best Prompts** for Claude Code CLI.

These are optimized to handle the complexity of mixing Python (AI) and Node.js (Auth) while ensuring the "Personalization" feature uses the correct Model via OpenRouter.

###1. Specification Prompt (`/spec`)*Run this first. It defines the "What" and "How" for both features.*

```markdown
/spec
**OBJECTIVE:**
Define the architecture for **Phase 3: User Authentication & Content Personalization**.

**CONTEXT:**
We are adding a "Hybrid Microservice" layer to our existing Docusaurus + FastAPI project.
1.  **Auth Service:** A lightweight Node.js/Hono service using `better-auth`.
2.  **AI Service:** The existing Python FastAPI backend.
3.  **Database:** Shared Neon Postgres (both services connect here).

**REQUIREMENT 1: Authentication & Data Collection**
* **Tool:** Use `better-auth` (TypeScript).
* **Schema Extension:** The `user` table MUST store:
    * `software_background` (Enum: "Beginner", "Intermediate", "Advanced")
    * `hardware_background` (Enum: "None", "Arduino", "RaspberryPi")
    * `learning_goal` (Text)
* **UX:** On "Sign Up", prompt the user to fill these fields.

**REQUIREMENT 2: Personalization Engine**
* **Trigger:** A "Personalize Chapter" button on the Frontend.
* **Flow:**
    1.  Frontend sends `chapter_content` + `user_id` to Python Backend.
    2.  Python Backend fetches user's `software_background` from DB.
    3.  **AI Processing:**
        * **Provider:** OpenRouter.
        * **Model:** Use a **Free/Low-cost Large Context Model** (e.g., `meta-llama/llama-3.1-70b-instruct` or `qwen/qwen-2.5-72b-instruct`). **DO NOT use Gemini.**
        * **Prompt:** "Rewrite this content for a user who is a [Level] in software..."

**OUTPUT:**
* Define the Shared Database Schema (SQL).
* Define the API Contract for the new Node Auth Service.
* Define the API Contract for the Python Personalization Endpoint.

```

---

###2. Implementation Plan Prompt (`/plan`)*Run this after the spec is generated. It enforces the "Sequential" strategy we discussed.*

```markdown
/plan
**ACTION REQUIRED:**
Generate the Implementation Roadmap for **Phase 3**.

**STRATEGY:**
Execute strictly in order: **Data Collection (Auth)** first, then **Data Usage (Personalization)**.

**Sub-Phase 3.1: SCAFFOLD Auth Service (Node.js)**
1.  **Create** `/auth-service` directory (outside `/backend`).
2.  **Initialize** Node.js project with `hono`, `better-auth`, `pg`, `dotenv`.
3.  **Database:** Connect to the **existing Neon Postgres** (Share `DATABASE_URL` from Phase 2).
4.  **Schema Migration:** Apply schema updates (User table + Background fields) to Postgres.

**Sub-Phase 3.2: INTEGRATE Frontend Auth**
5.  **Install** `@better-auth/react` (or appropriate client) in Docusaurus.
6.  **Build** `AuthModal.tsx`:
    * **Sign In:** Standard Email/Pass.
    * **Sign Up:** Email/Pass + **Select Inputs** for Software/Hardware background.
7.  **Verification:** Test User Signup and verify data appears in Neon DB tables.

**Sub-Phase 3.3: BUILD Personalization Backend (Python)**
8.  **Update** Python Requirements: Ensure `asyncpg` or `sqlalchemy` can read the new User table.
9.  **Implement** `POST /api/personalize`:
    * **Fetch:** Retrieve `software_background` using `user_id`.
    * **Generate:** Call OpenRouter (Llama 3.1 70B or Qwen 72B).
    * **Constraint:** Handle large inputs (Chapter text) by checking token limits.

**Sub-Phase 3.4: FRONTEND "Magic Button"**
10. **Swizzle** Docusaurus `DocItem` layout.
11. **Inject** "✨ Personalize for Me" button at the top of the page.
12. **State Management:**
    * If Logged Out -> Open AuthModal.
    * If Logged In -> Call `/api/personalize` and replace text with streaming response.

```

###Why these are the "Best":1. **Explicit Model Choice:** I explicitly said **"DO NOT use Gemini"** and suggested **Llama 3.1 / Qwen 72B** via OpenRouter, which are excellent, have large context windows, and are often free/cheap.
2. **Microservice Clarity:** It tells the AI exactly where to put the new code (`/auth-service` vs `/backend`), preventing file structure mess.
3. **Database Safety:** It emphasizes connecting to the **existing** database, so you don't accidentally create a second empty database.

**Ready to paste the `/spec` command?**