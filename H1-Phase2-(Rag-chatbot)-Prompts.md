# Specification
"""

Physical AI Textbook - Phase 2: RAG Chatbot Integration (Hybrid Edition)
**Objective:** Architect and integrate a Retrieval-Augmented Generation (RAG) chatbot using the OpenAI Agents/ChatKit SDK, powered by a hybrid model stack.

**Core Requirement (Critical):**
* **Context7 MCP Usage:** You MUST use the `context7` tool to fetch the latest docs for OpenAI Agents SDK and OpenRouter integration standards before coding.

**Technical Architecture:**
* **Frontend:** React component embedded in Docusaurus Layout (Floating Widget).
* **UI Layout (CRITICAL):** The Chat Widget must use **CSS Fixed Positioning** (Overlay) to float above the content (z-index: 9999). It must NEVER be rendered as a static block in the page footer.
* **Backend API:** FastAPI service.
* **Vector Database:** Qdrant Cloud (Free Tier).
* **Relational Database:** Neon Serverless Postgres.
* **AI Model Stack (Hybrid):**
  - **Generation:** `qwen/qwen2.5-7B-instruct` via **OpenRouter API**.
  - **Embeddings:** `text-embedding-004` via **Google Gemini API**.

**Success Criteria:**
1. **Accurate Retrieval:** Ingestion script uses `text-embedding-004` to vectorize book content.
2. **OpenRouter Integration:** The Chatbot successfully answers using the Qwen 2.5 model via OpenRouter.
3. **Contextual Logic:** Correctly handles "Selected Text" queries (answering based ONLY on the user's highlight).

**Constraints:**
* Use **GEMINI_API_KEY** for embeddings.
* Use **OPENROUTER_API_KEY** for text generation.
* Use **Neon Serverless Postgres** for session storage.
* Must NOT break the existing Phase 1 Docusaurus build.

**Do not generate any code or detailed plans yet.**

"""

# Plan

"""
/plan
**Objective:** Create a comprehensive Implementation Plan for Phase 2: Integrated RAG Chatbot (Hybrid Architecture).

**Context:**
* We are building a "Floating Chat Widget" for our Docusaurus book.
* **Architecture:** Hybrid AI Stack.
  - **Embeddings:** `text-embedding-004` (via Google Gemini API).
  - **Generation:** `qwen/Qwen2.5-7B-Instruct` (via OpenRouter API).
* **Tools:** Context7 MCP (for docs), Neon Postgres (History), Qdrant (Vectors), FastAPI (Backend).

**Requirement:**
Generate a detailed task list that covers these 4 sub-phases in order.

### **Sub-Phase 2.1: Backend Infrastructure**
1.  **Project Structure:** Create `/backend` with `requirements.txt` (fastapi, uvicorn, qdrant-client, sqlalchemy, openai, google-generativeai).
2.  **Environment:** Setup `.env` template with `GEMINI_API_KEY` and `OPENROUTER_API_KEY`.
3.  **Database Config:**
    * Setup `backend/db/postgres.py` (Neon/SQLAlchemy).
    * Setup `backend/db/qdrant.py` (Connect to Qdrant Cloud).
    * **Task:** Create a Qdrant collection named `textbook_chunks` with vector size **768**.

### **Sub-Phase 2.2: The Knowledge Pipeline (Ingestion)**
4.  **Scraper Script:** Create `backend/scripts/ingest.py` to read all `.md` files from `/docs`.
5.  **Vectorization:**
    * Use `google.generativeai` to embed text chunks using `models/text-embedding-004`.
    * **Context7 Instruction:** Fetch latest Google GenAI python docs before writing this.
6.  **Storage:** Upsert vectors + metadata (chapter title, source URL) to Qdrant.

### **Sub-Phase 2.3: The "Brain" (AI Logic)**
7.  **Agent Setup:**
    * Create `backend/agent/bot.py`.
    * Configure OpenAI SDK to point to **OpenRouter** (`https://openrouter.ai/api/v1`) using `qwen/Qwen2.5-7B-Instruct`.
    * **Context7 Instruction:** Fetch "OpenAI SDK with OpenRouter" docs first.
8.  **RAG Tool:** Implement `search_knowledge_base` using Gemini embeddings to query Qdrant.
9.  **Contextual Logic:**
    * Implement logic to handle `selected_text`.
    * *Rule:* If `selected_text` is present, prompt model to "Answer ONLY based on this text".
10. **API Endpoint:** Create `POST /api/chat` (Session management + Agent response).

### **Sub-Phase 2.4: Frontend Widget (The UI)**
11. **Chat Component:**
    * Create `src/components/ChatWidget/index.tsx`.
    * **CRITICAL CSS:** Force the widget to float using `position: fixed; bottom: 20px; right: 20px; z-index: 9999`. It must NEVER sit in the footer.
12. **Selection Listener:** Add `useEffect` to capture `window.getSelection()` text.
13. **Integration:** Swizzle Docusaurus `<Layout>` to mount the widget globally.

**Output:**
Generate the complete task list (T-001 to T-xxx) so I can execute them sequentially.

"""