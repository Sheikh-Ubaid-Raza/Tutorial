Here are the three finalized, optimized prompts for your **Hackathon Project – Phase 1**.

I have reviewed them against your requirements and the source text. They are structured to force Claude Code to adhere to strict architecture rules, clearly define the scope (Phase 1 only), and generate a specific, actionable implementation plan with the correct course curriculum.

You can copy and paste these into the Claude Code CLI one by one.

### **Step 1: Set the Project Constitution**

*Use this first to establish the global rules, tech stack, and quality standards for the entire project.*

```text
/sp.constitution
**Project:** Physical AI & Humanoid Robotics Textbook (Hackathon I)

**Core Principles:**
1. **AI-Native Workflow:** All major features must be architected using Spec-Kit Plus specifications before implementation.
2. **Educational Clarity:** Code structure must be pedagogical; content must be accessible to students using the defined "Physical AI" curriculum.
3. **Modularity:** Strict separation between the Content Layer (Docusaurus), Intelligence Layer (RAG/Agents), and Auth Layer.

**Technology & Architecture Standards:**
* **Frontend/Content:** Docusaurus v3 (React/TypeScript). Content written in Markdown/MDX with Mermaid diagrams.
* **Backend/RAG:** Python (FastAPI) integrated with OpenAI Agents SDK.
* **Database:** Neon Serverless Postgres (Relational) & Qdrant Cloud (Vector).
* **Authentication:** Better-Auth implementation with mandatory user profiling (Hardware/Software background).

**Coding & Quality Rules:**
* **Type Safety:** Strict TypeScript for frontend; Type hints for Python backend.
* **Secrets Management:** API Keys (OpenAI, Qdrant, Database) must NEVER be hardcoded. Use `.env` files exclusively.
* **Component Reuse:** UI components (e.g., "Translate Button", "Personalize Button") must be reusable across chapters.
* **Reusable Intelligence:** Logic must be encapsulated into reusable Claude Code Subagents and Agent Skills where possible.

**Directory Structure Enforcement:**
* `/docs`: Textbook chapters (Markdown/MDX).
* `/src`: React components and custom Docusaurus pages.
* `/backend`: FastAPI, RAG logic, and Agent definitions.
* `/specs`: Spec-Kit Plus documentation and architectural blueprints.

**Success Criteria:**
1. Successful build and deployment to GitHub Pages.
2. Functional RAG Chatbot capable of answering from selected text.
3. Zero critical security vulnerabilities (verified via audit).
4. Lighthouse Performance score > 90.
```

-----

### **Step 2: Define Phase 1 Specification**

*Use this second. It tells Claude that "right now," we are ONLY focusing on the book creation and deployment, ignoring the complex backend for now.*

```text
/sp.specify Physical AI & Humanoid Robotics Textbook (Phase 1: Foundation & Deployment)
**Target Audience:** Students and engineers learning embodied intelligence, ROS 2, and NVIDIA Isaac Sim.
**Focus:** Initializing the Docusaurus framework, structuring the curriculum, and establishing the CI/CD pipeline to GitHub Pages.

**Success Criteria:**
* **Live Deployment:** A functional, publicly accessible Docusaurus site hosted on GitHub Pages.
* **Curriculum Structure:** Navigation sidebar accurately reflects the 4 Modules and 13-Week breakdown defined in the course syllabus.
* **Content Generation:** Initial chapters drafted using Spec-Kit Plus and Claude Code, covering "Physical AI" fundamentals.
* **Repo Health:** Public GitHub repository established with clean commit history.

**Constraints:**
* **Framework:** Must use Docusaurus v3 (React/TypeScript).
* **Tooling:** Content and structure must be generated via Spec-Kit Plus and Claude Code CLI.
* **Hosting:** Must deploy specifically to GitHub Pages.
* **Deadline:** Foundation must be ready well before the final Nov 30, 2025 submission.

**Not Building (Phase 2/3 Non-Goals):**
* Integrated RAG Chatbot (OpenAI/Qdrant integration).
* User Authentication (Better-Auth Signup/Signin).
* Dynamic Personalization or Urdu Translation buttons.
* Interactive Coding Exercises (embedded).
```

-----

### **Step 3: Generate Implementation Plan**

*Use this last. It provides the detailed syllabus so Claude generates the exact folder structure and files you need.*

```text
/plan
**Objective:** Create a comprehensive implementation plan for **Phase 1: Foundation & Deployment** of the "Physical AI & Humanoid Robotics" textbook.

**Context:**
* **Source:** References the approved `/sp.specify` for Phase 1 (Book Creation & Deployment).
* **Tooling:** Uses Spec-Kit Plus for structure and Context7 MCP for the latest Docusaurus v3 documentation.
* **Constraint:** Strictly limited to content creation and hosting. No Chatbot, Auth, or Backend logic in this phase.

**Tech Stack (Phase 1):**
* **Framework:** Docusaurus v3 (React/TypeScript).
* **Content:** Markdown/MDX with Mermaid.js diagrams.
* **Styling:** Custom CSS/Infima (Docusaurus default).
* **CI/CD:** GitHub Actions for automated build/deploy.
* **Hosting:** GitHub Pages.

**Required Plan Sections:**

1. **Project Initialization:**
   * Command sequence to scaffold a new Docusaurus site using TypeScript.
   * Cleanup of default template (blog, tutorial remnants).
   * Installation of essential plugins (e.g., `docusaurus-plugin-redoc` or similar if needed).

2. **Architecture & Taxonomy:**
   * **Directory Structure:** Define the exact folder hierarchy for the 4 Modules and 13 Weeks (e.g., `/docs/module-01/week-01/`).
   * **Sidebar Config:** Strategy for `sidebars.ts` to auto-generate navigation based on the "Physical AI" curriculum.

3. **Content Templates:**
   * Create a reusable MDX template for chapters (`_template.mdx`) including standard headers (Learning Outcomes, Prerequisites, Core Concepts).
   * Define standards for code blocks (syntax highlighting for Python/C++ ROS nodes).

4. **DevOps & Deployment:**
   * **Git Setup:** Repo initialization and `.gitignore` configuration (node_modules, build artifacts).
   * **CI/CD Workflow:** Provide the exact YAML configuration for `.github/workflows/deploy.yml` to build and deploy to the `gh-pages` branch on push to `main`.
   * **Docusaurus Config:** Required settings in `docusaurus.config.ts` for GitHub Pages (baseUrl, organizationName, projectName).

5. **Execution Steps:**
   * A numbered list of CLI commands I can copy-paste to execute this entire setup from zero to live URL.

## Course Syllabus (Detailed Content Architecture)
Use this structure to generate directories and seed chapter content:

**Module 1: The Robotic Nervous System (ROS 2)**
* Weeks 1-2: Introduction to Physical AI
  - Foundations of embodied intelligence and physical laws
  - Sensor systems: LIDAR, cameras, IMUs, force/torque sensors
* Weeks 3-5: ROS 2 Fundamentals
  - ROS 2 architecture, Nodes, topics, services, and actions
  - Building ROS 2 packages with Python and Launch files

**Module 2: The Digital Twin (Gazebo & Unity)**
* Weeks 6-7: Robot Simulation
  - Gazebo simulation environment setup
  - URDF and SDF robot description formats
  - Physics simulation and Introduction to Unity for visualization

**Module 3: The AI-Robot Brain (NVIDIA Isaac)**
* Weeks 8-10: NVIDIA Isaac Platform
  - NVIDIA Isaac SDK and Isaac Sim setup
  - AI-powered perception, manipulation, and Reinforcement learning
  - Sim-to-real transfer techniques

**Module 4: Vision-Language-Action (VLA)**
* Weeks 11-12: Humanoid Robot Development
  - Kinematics, dynamics, and Bipedal locomotion
  - Manipulation, grasping, and Natural human-robot interaction
* Week 13: Conversational Robotics
  - Integrating GPT models for conversational AI
  - Multi-modal interaction: speech, gesture, vision

**Output Format:**
Return a structured Markdown document with clear headers, code snippets for config files, and a sequential checklist for execution.
```