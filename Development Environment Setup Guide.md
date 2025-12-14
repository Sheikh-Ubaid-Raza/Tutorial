# Development Environment Setup Guide for Beginners

This comprehensive guide will walk you through installing essential development tools on Windows. Follow each section in order for the best results.

---

## 1. Python Installation

Python is a versatile programming language used for web development, data science, AI, and more.

### Steps:

1. **Download Python**
   - Visit the official Python website: [python.org/downloads](https://www.python.org/downloads/)
   - Click the yellow "Download Python" button (latest version recommended)

2. **Run the Installer**
   - Locate the downloaded file (usually in your Downloads folder)
   - Double-click the `.exe` file to start installation
   - **IMPORTANT**: Check the box that says "Add Python to PATH" at the bottom of the installer window
   - Click "Install Now"

3. **Verify Installation**
   - Open Command Prompt (press `Win + R`, type `cmd`, press Enter)
   - Type the following command and press Enter:
     ```bash
     python --version
     ```
   - You should see the Python version number (e.g., `Python 3.12.0`)

4. **Verify pip (Python Package Manager)**
   - In the same Command Prompt, type:
     ```bash
     pip --version
     ```
   - You should see the pip version information

**Troubleshooting**: If commands aren't recognized, restart your computer and try again.

---

## 2. Node.js and npm Installation

Node.js allows you to run JavaScript on your computer, and npm is its package manager for installing libraries.

### Steps:

1. **Download Node.js**
   - Visit: [nodejs.org](https://nodejs.org/)
   - Download the **LTS (Long Term Support)** version (recommended for most users)

2. **Run the Installer**
   - Double-click the downloaded `.msi` file
   - Click "Next" through the installation wizard
   - Accept the license agreement
   - Keep the default installation path
   - Make sure "npm package manager" is checked
   - Click "Install"

3. **Verify Installation**
   - Open a new Command Prompt window
   - Check Node.js version:
     ```bash
     node --version
     ```
   - Check npm version:
     ```bash
     npm --version
     ```
   - Both commands should display version numbers

**Note**: Always open a new terminal window after installation to ensure PATH changes take effect.

---

## 3. WSL Ubuntu Installation for Windows

WSL (Windows Subsystem for Linux) lets you run Linux directly on Windows without a virtual machine.

### Why Do You Need WSL Ubuntu?

**For Developers, WSL is Essential Because:**

1. **Linux-based Development Tools**: Many modern development tools, frameworks, and AI coding assistants (like Claude Code) work best on Linux/Unix systems. WSL gives you access to these tools while staying on Windows.

2. **Real-World Environment**: Most servers and production environments run on Linux. WSL lets you develop and test in an environment similar to where your code will actually run.

3. **Better Command-Line Tools**: Linux has powerful built-in tools for file manipulation, text processing, and automation that are standard in the development world.

4. **Docker and Containers**: If you plan to work with Docker or containerized applications, WSL 2 provides native support and better performance.

5. **Cross-Platform Development**: Write code once and run it on both Windows and Linux without compatibility issues.

6. **Package Managers**: Linux package managers (like apt) make installing development tools much easier than on Windows.

**Specific Use Cases:**
- Running Node.js projects that have Linux dependencies
- Using Python libraries that require Linux compilation
- Working with Git and version control more efficiently
- Testing your code in a Linux environment before deployment
- Using shell scripts (bash) that are standard in the industry

**When You Might Not Need It:**
- If you only develop Windows desktop applications
- If you're just learning programming basics with Python or JavaScript
- If your projects are purely web-based with no Linux-specific dependencies

However, for modern full-stack development and working with AI tools like Claude Code, having WSL Ubuntu is highly recommended.

### Prerequisites:
- Windows 10 version 2004 or higher, or Windows 11
- Administrator access on your computer

### Steps:

1. **Install WSL with Ubuntu**
   - Open PowerShell or Command Prompt **as Administrator** (right-click and select "Run as administrator")
   - Run this single command:
     ```bash
     wsl --install
     ```
   - This will install WSL and Ubuntu by default
   - Wait for the installation to complete (may take several minutes)

2. **Restart Your Computer**
   - Restart when prompted

3. **Set Up Ubuntu**
   - After restart, Ubuntu will automatically open
   - Create a username (lowercase, no spaces) and password
   - **IMPORTANT**: Your password won't show as you type (this is normal for Linux)
   - Remember these credentials!

4. **Update Ubuntu**
   - Once inside Ubuntu terminal, run:
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Enter your password when prompted

5. **Verify Installation**
   - Check WSL version:
     ```bash
     wsl --version
     ```
   - List installed distributions:
     ```bash
     wsl --list --verbose
     ```

### Optional: Install Ubuntu Desktop App

For a better experience with a graphical interface:

1. Visit: [ubuntu.com/desktop/wsl](https://ubuntu.com/desktop/wsl)
2. Download the Ubuntu Desktop app from Microsoft Store
3. Launch and follow on-screen instructions

### Accessing WSL Ubuntu:
- Open "Ubuntu" from Start Menu, or
- Type `wsl` in any Command Prompt/PowerShell, or
- Use Windows Terminal (recommended)

**Reference**: [Microsoft WSL Documentation](https://learn.microsoft.com/en-us/windows/wsl/install)

---

## 4. Claude Code Installation

Claude Code is an AI-powered command-line tool for developers.

### Installation on Windows

1. **Open Command Prompt or PowerShell**

2. **Install Claude Code via npm**
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```

3. **Verify Installation**
   ```bash
   claude --version
   ```

4. **Authenticate Claude Code**
   - Run:
     ```bash
     claude auth
     ```
   - Follow the prompts to log in with your Anthropic account
   - A browser window will open for authentication
   - Complete the login process

### Installation on WSL Ubuntu (Bash)

1. **Open WSL Ubuntu Terminal**

2. **Ensure Node.js and npm are installed in WSL**
   - If not already installed, run:
     ```bash
     curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
     sudo apt-get install -y nodejs
     ```

3. **Install Claude Code**
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```

4. **Verify Installation**
   ```bash
   claude --version
   ```

5. **Authenticate**
   ```bash
   claude auth
   ```

**Reference**: [Claude Code Installation Guide](https://ai-native.panaversity.org/docs/AI-Tool-Landscape/claude-code-features-and-workflows/installation-and-authentication)

---

## 5. Claude Code Router Installation

Claude Code Router helps manage multiple AI coding assistants.

### Installation:

1. **Open Command Prompt, PowerShell, or WSL Terminal**

2. **Install via npm**
   ```bash
   npm install -g @musistudio/claude-code-router
   ```

3. **Verify Installation**
   ```bash
   ccr --version
   ```

**Note**: This tool works on both Windows and WSL once installed.

---

## 6. Qwen CLI Installation

Qwen is another AI coding assistant that can work alongside Claude Code.

### Installation:

1. **Open Command Prompt, PowerShell, or WSL Terminal**

2. **Install via npm**
   ```bash
   npm install -g @qwen-code/qwen-code@latest
   ```

3. **Verify Installation**
   ```bash
   qwen --version
   ```

---

## 7. SpecKit Plus Installation

SpecKit Plus is a powerful specification-driven development tool that helps you plan, design, and implement software projects systematically using AI assistance.

### Why Do You Need SpecKit Plus?

**SpecKit Plus is Essential for Structured Development:**

1. **Specification-Driven Development (SDD-RI)**: Instead of jumping straight into coding, SpecKit Plus helps you define clear specifications first, reducing bugs and rework.

2. **AI-Powered Planning**: Uses AI to help you break down complex projects into manageable tasks and steps through structured workflows.

3. **Constitution-Based Development**: Define your project's core principles, requirements, and constraints upfront for consistent decision-making throughout development.

4. **Systematic Workflow**: Guides you through a proven development process: constitution → specify → clarify → plan → tasks → implement → analyze.

5. **Better Communication**: Creates clear documentation that helps teams (or AI assistants) understand project requirements precisely.

6. **Quality Assurance**: Built-in analysis commands help catch issues before they become problems.

7. **Reusable Intelligence**: Capture architectural decisions (ADRs) and prompt history (PHRs) to build organizational knowledge.

**Perfect For:**
- Building complex applications with multiple features
- Working with AI coding assistants like Claude Code or Gemini CLI
- Team projects requiring clear specifications
- Learning software engineering best practices
- Freelancers who need to document client requirements
- Anyone following specification-driven development methodology

### Prerequisites:

**Python 3.12 or higher is required** for SpecKit Plus. Make sure you've completed Section 1 (Python Installation) before proceeding.

**Check your Python version:**
```bash
python --version
```

You should see `Python 3.12.0` or higher. If you have Python 3.11 or lower, upgrade Python first.

### Installation:

1. **Open Command Prompt, PowerShell, or WSL Terminal**

2. **Install SpecKit Plus via pip**
   ```bash
   pip install specifyplus
   ```

3. **Verify Installation**
   ```bash
   specifyplus --version
   ```

**Important Note**: SpecKit Plus is the **framework** that provides structure and commands. You still need an **AI tool** (like Claude Code or Gemini CLI) to execute those commands. Think of it as:
- **SpecKit Plus** = The workflow and templates
- **Claude Code/Gemini CLI** = The AI brain that follows the workflow

### Initialize Your First Project:

Once installed, create a test project to verify everything works:

```bash
# Create a new project
specifyplus init my-first-project

# Navigate to the project
cd my-first-project
```

**During initialization, you'll be asked:**
- **Select AI Tool**: Choose `Claude Code` (recommended) or `Gemini CLI`
- **Select Terminal**: Choose `bash` (or `powershell` on Windows without WSL)

### Project Structure:

After initialization, your project will have this structure:

```
my-first-project/
├── .claude/
│   └── commands/              # Slash commands for your workflow
│       ├── sp.constitution.md # Create project constitution
│       ├── sp.specify.md      # Write specifications
│       ├── sp.clarify.md      # Clarify requirements
│       ├── sp.plan.md         # Generate plans
│       ├── sp.tasks.md        # Break into tasks
│       ├── sp.implement.md    # Execute implementation
│       ├── sp.analyze.md      # Analyze code/specs
│       ├── sp.adr.md          # Document decisions
│       └── sp.phr.md          # Record prompt history
│
├── .specify/
│   ├── memory/
│   │   └── constitution.md    # Project-wide rules
│   ├── scripts/               # Automation scripts
│   └── templates/             # Templates for specs, plans, etc.
│
├── .git/                      # Git repository (auto-initialized)
├── CLAUDE.md                  # Agent instructions
├── README.md                  # Project documentation
└── .gitignore
```

### Verify Commands Work:

1. **Launch your AI tool** in the project directory:
   ```bash
   claude
   ```
   (or `gemini` if using Gemini CLI)

2. **Test slash command access** by typing:
   ```
   /sp.
   ```

You should see all SpecKit Plus commands appear as autocomplete suggestions!

### SpecKit Plus Commands Reference

SpecKit Plus provides a structured workflow through these powerful commands:

#### `/sp.constitution`
**Purpose**: Define your project's foundation and core principles

**What it does:**
- Creates a "constitution" document that outlines project goals, constraints, and requirements
- Establishes guiding principles for all development decisions
- Defines what's in scope and out of scope
- Sets quality standards and technical constraints
- Stored in `.specify/memory/constitution.md` and referenced throughout development

**When to use**: At the very start of any new project, before writing any code

**Example usage**:
```bash
/sp.constitution "Build a task management app for students with offline support"
```

---

#### `/sp.specify`
**Purpose**: Create detailed specifications for features or components

**What it does:**
- Generates comprehensive technical specifications
- Defines inputs, outputs, and behavior
- Documents API contracts and data structures
- Specifies functional and non-functional requirements
- Creates spec files in the `specs/` directory
- Ensures specifications align with project constitution

**When to use**: After constitution, when you need to detail specific features

**Example usage**:
```bash
/sp.specify "User authentication system with email, password, and 2FA"
```

---

#### `/sp.clarify`
**Purpose**: Ask questions and resolve ambiguities in specifications

**What it does:**
- Identifies unclear or ambiguous parts of your spec
- Asks relevant questions to fill knowledge gaps
- Helps you think through edge cases
- Refines requirements based on your answers
- Validates specifications for completeness
- Updates spec files with clarifications

**When to use**: After specifying, to ensure everything is crystal clear before planning

**Example usage**:
```bash
/sp.clarify "What happens if user forgets password? How long should reset tokens be valid?"
```

---

#### `/sp.plan`
**Purpose**: Create a step-by-step implementation plan

**What it does:**
- Breaks down specifications into actionable steps
- Orders tasks logically (identifies what must be done first)
- Identifies dependencies between components
- Estimates complexity and suggests milestones
- Creates plan files that reference specifications
- Documents architectural decisions needed

**When to use**: After specifications are clarified, before actual implementation

**Example usage**:
```bash
/sp.plan "Implement the user authentication system from spec"
```

---

#### `/sp.tasks`
**Purpose**: Generate a detailed task list from your plan

**What it does:**
- Converts high-level plans into specific, actionable tasks
- Creates atomic work units with clear completion criteria
- Breaks large tasks into smaller, manageable pieces
- Suggests task priorities and order
- Generates checkpoint-based workflow
- Creates task files that can be tracked

**When to use**: After planning, when you're ready to start coding

**Example usage**:
```bash
/sp.tasks "Break down authentication implementation into tasks"
```

---

#### `/sp.implement`
**Purpose**: Execute tasks with AI collaboration

**What it does:**
- Guides implementation of specific tasks from task list
- Generates actual code following your specifications
- Implements features according to the plan
- Follows the constitution's principles and constraints
- Creates production-ready, tested code
- Updates task status as work progresses

**When to use**: After planning and task breakdown, during active development

**Example usage**:
```bash
/sp.implement "Create the login endpoint with JWT tokens"
```

---

#### `/sp.analyze`
**Purpose**: Review and analyze existing code or specifications

**What it does:**
- Examines code for potential issues or improvements
- Checks if implementation matches specifications
- Validates cross-artifact consistency
- Identifies security vulnerabilities or performance issues
- Suggests refactoring opportunities
- Ensures alignment with project constitution

**When to use**: During or after implementation to ensure quality

**Example usage**:
```bash
/sp.analyze "Review authentication module for security and compliance with spec"
```

---

#### `/sp.adr`
**Purpose**: Document architectural decisions (ADR = Architectural Decision Record)

**What it does:**
- Records important technical decisions and their rationale
- Captures context: why the decision was made
- Documents alternatives considered
- Explains consequences and trade-offs
- Stores decisions in `history/adr/` for future reference
- Builds organizational knowledge over time

**When to use**: When making significant architectural or technical decisions

**Example usage**:
```bash
/sp.adr "Why we chose JWT over session-based authentication"
```

---

#### `/sp.phr`
**Purpose**: Record prompt history (PHR = Prompt History Record)

**What it does:**
- Captures important AI collaboration sessions
- Documents prompts that led to breakthroughs
- Records context and reasoning behind decisions
- Stores in `history/prompts/` for reuse
- Creates reusable intelligence for future projects
- Helps teams learn from past AI interactions

**When to use**: After significant AI-assisted problem-solving sessions

**Example usage**:
```bash
/sp.phr "Document how we solved the password reset race condition"
```

---

### SpecKit Plus Workflow Example

Here's how you'd use SpecKit Plus commands in sequence for a real project:

```bash
# 1. Initialize project
specifyplus init blog-platform
cd blog-platform
claude  # Launch Claude Code

# 2. Define project foundation
/sp.constitution "Build a blog platform for developers with markdown support, SEO optimization, and comment system"

# 3. Specify your first major feature
/sp.specify "Article creation and editing system with markdown support, draft saving, and auto-save"

# 4. Clarify any ambiguities
/sp.clarify "Should auto-save work offline? What's the conflict resolution strategy?"

# 5. Create implementation plan
/sp.plan "Article creation system"

# 6. Document key architectural decision
/sp.adr "Why we chose IndexedDB for offline storage instead of localStorage"

# 7. Break plan into atomic tasks
/sp.tasks "Article creation implementation"

# 8. Implement the feature task by task
/sp.implement "Task 1: Create article schema and database models"
/sp.implement "Task 2: Build article editor component"
/sp.implement "Task 3: Implement auto-save functionality"

# 9. Analyze the implementation
/sp.analyze "Check article system for security, performance, and spec compliance"

# 10. Record successful prompts for reuse
/sp.phr "Document the markdown parsing and sanitization solution"
```

This systematic approach ensures you build software thoughtfully, not haphazardly!

---

### Understanding Key Directories

| Directory | Purpose |
|-----------|---------|
| `.claude/commands/` | Slash commands you'll use throughout the SDD workflow |
| `.specify/memory/` | Your project constitution (created once, referenced always) |
| `.specify/scripts/` | Automation scripts for PHRs, ADRs, and feature setup |
| `.specify/templates/` | Templates that guide spec, plan, task, ADR, and PHR creation |
| `specs/` | Your feature specifications (created when you run `/sp.specify`) |
| `history/adr/` | Architectural Decision Records |
| `history/prompts/` | Prompt History Records for reusable intelligence |
| `CLAUDE.md` | Agent instructions that guide your AI collaborator |

---

### Common Mistakes to Avoid

**Mistake 1: Confusing SpecKit Plus with Claude Code**
- SpecKit Plus is the **framework** (workflow and commands)
- Claude Code is the **AI tool** that executes the framework
- You need **BOTH** installed to work effectively

**Mistake 2: Skipping Project Initialization**
- Don't create folders manually
- Always use `specifyplus init <project-name>` to get proper structure

**Mistake 3: Wrong Python Version**
- SpecKit Plus requires Python 3.12+
- Check with `python --version` before installing

**Mistake 4: Not Running Commands in Project Directory**
- Always `cd` into your project directory before launching Claude Code
- Commands need access to `.claude/commands/` and `.specify/` folders

**Reference**: [SpecKit Plus Installation Guide](https://ai-native.panaversity.org/docs/SDD-RI-Fundamentals/spec-kit-plus-hands-on/installation-and-setup)

---

## Combined Installation Command

You can install all tools (Claude Code, Claude Code Router, and Qwen CLI) at once:

```bash
npm install -g @qwen-code/qwen-code@latest @anthropic-ai/claude-code @musistudio/claude-code-router
```

**Note**: SpecKit Plus is installed separately via pip (not npm) since it's a Python package.

---

## Post-Installation Checklist

Verify everything is installed correctly by running these commands:

```bash
# Check Python
python --version
pip --version

# Check Node.js and npm
node --version
npm --version

# Check WSL (from PowerShell/CMD on Windows)
wsl --version

# Check Claude Code
claude --version

# Check Claude Code Router
ccr --version

# Check Qwen CLI
qwen-code --version

# Check SpecKit Plus
specifyplus --version
```

All commands should return version numbers without errors.

---

## Common Troubleshooting

### "Command not found" errors:
- Close and reopen your terminal
- Make sure you installed with `-g` (global) flag
- On Windows, try running PowerShell as Administrator
- Check if npm global path is in your PATH environment variable

### npm permission errors on Linux/WSL:
- Don't use `sudo` with npm install -g if possible
- Configure npm to use a different directory: [npm docs](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)

### WSL issues:
- Make sure virtualization is enabled in BIOS
- Update Windows to the latest version
- Run `wsl --update` in PowerShell as Administrator

---

## Additional Resources

- **Python Documentation**: [docs.python.org](https://docs.python.org/)
- **Node.js Documentation**: [nodejs.org/docs](https://nodejs.org/docs/)
- **WSL Documentation**: [learn.microsoft.com/windows/wsl](https://learn.microsoft.com/en-us/windows/wsl/)
- **Claude Code Guide**: [AI Native Panaversity](https://ai-native.panaversity.org/)
- **GitHub Tutorial Repository**: [Q4 Learning](https://github.com/DanielHashmi/Q4_learning/tree/main/spec-driven-development/tutorials)

---

## Next Steps

Once everything is installed:

1. Try creating a simple Python script
2. Initialize a Node.js project with `npm init`
3. Experiment with Claude Code and Qwen CLI for AI-assisted coding
4. Explore WSL Ubuntu and get comfortable with Linux commands
5. **Start your first project with SpecKit Plus**:
   - Create a project constitution
   - Specify a simple feature
   - Follow the workflow: constitution → specify → clarify → plan → tasks → implement → analyze
6. Practice using the SpecKit Plus commands to understand specification-driven development

Happy coding!