```
Deploy the Physical AI textbook project to GitHub Pages using the GitHub MCP server.

Context:
- GitHub MCP server is connected and authenticated
- GitHub CLI (gh) is not installed 
- Repository already exists: https://github.com/
- Local Docusaurus project is complete and tested on localhost
- GitHub Pages deployment configuration is already set in docusaurus.config.ts

Your task:
1. Initialize git repository in the project (if not already initialized)
2. Use GitHub MCP server to connect to the existing repository
3. Add all project files to git
4. Create initial commit with message "Initial commit: Physical AI textbook complete"
5. Push code to main branch
6. Trigger GitHub Actions deployment workflow (already configured in .github/workflows/deploy.yml)
7. Verify deployment is successful

Use the GitHub MCP server tools to handle all git operations and repository interactions.

Execute deployment now.
```

# Use OpenAI Agents SDK

Use OpenAI Agents SDK through Context7 MCP server for building the RAG chatbot agent.

REQUIREMENT:
- Access OpenAI Agents SDK via Context7 MCP server only
- Use OpenRouter API key (not OpenAI key)
- Use model: qwen/qwen-2.5-7b-instruct
- OpenAI Agents SDK is compatible with OpenRouter
- Do NOT use direct OpenAI client (openai.ChatCompletion, openai.OpenAI())
- All AI interactions must go through Context7 MCP

Implement RAG agent using Context7 MCP as the gateway to OpenAI Agents SDK with OpenRouter backend.