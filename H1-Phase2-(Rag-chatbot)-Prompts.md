Here are the finalized, execution-ready prompts for Phase 2. These incorporate all your requirements:

1.  **Floating Widget Guarantee:** Explicit CSS rules to prevent the "below footer" bug.
2.  **Gemini-Only Stack:** Using `gemini-2.0-flash` and `gemini-embedding-001`.
3.  **Context7 Enforcement:** Mandatory instructions to check docs before coding.
4.  **Step-by-Step Plans:** Modular approach for stability.

You can copy and paste these directly into Claude Code.

-----

### **1. Phase 2 Master Specification**

*Run this first. It defines the rules, architecture, and "Floating Widget" constraint.*

```text
/sp.specify Physical AI Textbook - Phase 2: RAG Chatbot Integration (Gemini Edition)
**Objective:** Architect and integrate a Retrieval-Augmented Generation (RAG) chatbot using the OpenAI Agents/ChatKit SDK, but powered by Google Gemini models.

**Core Requirement (Critical):**
* **Context7 MCP Usage:** Since OpenAI Agents SDK and ChatKit are bleeding-edge, you MUST use the `context7` tool to fetch their latest official documentation before proposing or writing any code. Do not rely on internal training data for syntax.

**Technical Architecture:**
* **Frontend:** React component embedded in Docusaurus Layout.
* **UI Layout (CRITICAL):** The Chat Widget must use **CSS Fixed Positioning** (Overlay) to float above the content. It must NEVER be rendered as a static block in the page footer.
* **Backend API:** FastAPI service.
* **Vector Database:** Qdrant Cloud (Free Tier).
* **Relational Database:** Neon Serverless Postgres.
* **Orchestration:** OpenAI Agents SDK / ChatKit.
* **AI Models (Google Gemini):**
  - **Generation:** `gemini-2.0-flash` (via OpenAI Compatibility or Native Integration).
  - **Embeddings:** `gemini-embedding-001` (for vectorization).

**Success Criteria:**
1. **Accurate Retrieval:** Ingestion script uses `gemini-embedding-001` to vectorize book content into Qdrant.
2. **Gemini Integration:** The Chatbot successfully answers using `gemini-2.0-flash`.
3. **Contextual Logic:** Correctly handles "Selected Text" queries (answering based ONLY on the user's highlight).
4. **Documentation Adherence:** Code structure strictly follows the latest patterns found via Context7.

**Constraints:**
* Use **GEMINI_API_KEY** exclusively (No OpenAI API Key).
* Use **Neon Serverless Postgres** for session storage.
* Must NOT break the existing Phase 1 Docusaurus build.
```

-----

### **2. Phase 2.1 Plan: Backend Infrastructure**

*Run this next to set up the server skeleton and database connections.*

```text
/plan
**Phase 2.1: Backend Infrastructure & Database Connection**
**Objective:** Initialize the FastAPI backend with Gemini and Database credentials.

**Tech Stack:**
* **Language:** Python 3.10+
* **Framework:** FastAPI
* **Databases:** Neon (Postgres) & Qdrant Cloud.

**Tasks:**
1. **Directory Setup:** Create `/backend` folder.
2. **Dependencies:** Create `requirements.txt` containing `fastapi`, `uvicorn`, `python-dotenv`, `psycopg2-binary`, `sqlalchemy`, `qdrant-client`, `openai` (for SDK compatibility), `google-generativeai`.
3. **Configuration:**
   - Create `.env` template.
   - **Crucial:** Variable `GEMINI_API_KEY` must be used.
4. **Database Logic:**
   - `backend/db/postgres.py`: SQLAlchemy setup for Neon.
   - `backend/db/qdrant.py`: Qdrant connection. Create collection `textbook_chunks` with vector size **768** (Standard for `gemini-embedding-001`).
5. **Health Check:** simple `/health` endpoint.

**Context7 Instruction:**
* Before writing `requirements.txt`, use Context7 to check if there are specific "adapter" packages needed to make OpenAI Agents SDK work with Gemini models.

**Output:**
Provide the full code structure and the CLI command to run the server locally.
```

-----

### **3. Phase 2.2 Plan: Ingestion Pipeline**

*Run this to scrape the book and fill the vector database.*

```text
/plan
**Phase 2.2: Ingestion Pipeline (Gemini Embeddings)**
**Objective:** Scrape the book and store vectors using `gemini-embedding-001`.

**Tasks:**
1. **Scraper Script:** `backend/scripts/ingest.py` to read `.md` files from `/docs`.
2. **Chunking:** Split text (approx 500-1000 chars).
3. **Vectorization (Gemini):**
   - Use `google.generativeai` (or compatible client) to generate embeddings.
   - **Model:** `models/gemini-embedding-001`.
4. **Storage:** Upsert vectors to Qdrant.
5. **Execution:** CLI command to run the script.

**Context7 Instruction:**
* Use Context7 to fetch the latest python syntax for `google-generativeai` embedding generation to ensure the script is 100% correct.

**Constraints:**
* Ensure vector dimensions in Qdrant match `gemini-embedding-001` output (768).
```

-----

### **4. Phase 2.3 Plan: AI Logic (The Brain)**

*Run this to build the Agent logic and "Selected Text" handling.*

```text
/plan
**Phase 2.3: RAG Logic & Chat Endpoint (Gemini + Agents SDK)**
**Objective:** Implement the RAG logic using OpenAI Agents SDK but routed to `gemini-2.0-flash`.

**Tasks:**
1. **Documentation Check (Mandatory):**
   - **ACTION:** Use Context7 to search "How to use OpenAI Agents SDK with Google Gemini models" or "OpenAI SDK base_url for Gemini".
   - Determine the correct configuration (e.g., setting `base_url` to Google's OpenAI-compatible endpoint).

2. **Tool Definition:**
   - Create `backend/agent/tools.py`.
   - Implement `search_knowledge_base`: Uses `gemini-embedding-001` to query Qdrant.

3. **Agent Logic (Context Prioritization):**
   - Create `backend/agent/bot.py`.
   - Initialize the Agent with **Model:** `gemini-2.0-flash`.
   - **Critical Logic:** The `chat` function must accept an optional `selected_text` parameter.
     - IF `selected_text` IS provided: Inject system instruction to "Answer ONLY based on the user's selected text: {selected_text}".
     - IF `selected_text` is EMPTY: Perform standard RAG retrieval using `search_knowledge_base`.

4. **API Endpoint:**
   - POST `/api/chat` accepting `{ session_id, message, selected_text }`.

**Output:**
Provide the exact Python code for `bot.py` and `tools.py` based on the Context7 findings.
```

-----

### **5. Phase 2.4 Plan: Frontend UI**

*Run this to build the floating widget and capture text selections.*

```text
/plan
**Phase 2.4: Frontend Widget & Selection Listener**
**Objective:** Connect the Docusaurus frontend to the Backend and capture user text selections.

**Tasks:**
1. **UI Component (Crucial Styling):**
   - Create `src/components/ChatWidget/index.tsx`.
   - **MANDATORY CSS:** The root container of this component MUST use:
     - `position: fixed`
     - `bottom: 20px`
     - `right: 20px`
     - `z-index: 9999`
   - This ensures it floats visually and is removed from the standard document flow (preventing the "below footer" bug).

2. **Selection Logic:** Implement a `useEffect` hook with `window.getSelection()` to capture text when a user highlights content in the book.

3. **API Integration:** Send the `selected_text` variable to the new Gemini-backed endpoint.

4. **Global Injection:**
   - Swizzle the Docusaurus Layout to ensure the widget appears on every page.
   - **Placement:** Render the `<ChatWidget />` as a direct child of the Layout container, but due to `position: fixed`, it will visually detach from the layout order.

**Context7 Instruction:**
* Use Context7 to fetch Docusaurus v3 "Swizzling" best practices to ensure the Layout wrapper is implemented safely without breaking the footer.

**Output:**
Provide the React code for the Widget and the Layout wrapper.
```