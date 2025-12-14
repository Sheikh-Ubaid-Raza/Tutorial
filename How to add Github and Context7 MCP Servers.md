### 1\. Add Context7 MCP Server

This server allows Claude to fetch up-to-date documentation.

**Command:**
Run this single command in your terminal:

```bash
claude mcp add context7 --transport http https://mcp.context7.com/mcp \
  --header "CONTEXT7_API_KEY: YOUR_API_KEY"
```

-----

### 2\. Add GitHub MCP Server

This connects Claude to your GitHub repository context.

#### **Step 1: Generate your GitHub Personal Access Token (PAT)**

1.  Log in to your **GitHub** account.
2.  Click on your **Profile Picture** (upper-right corner) → Select **Settings**.
3.  Scroll down the left sidebar to the bottom and click **Developer settings**.
4.  In the next left sidebar, click **Personal access tokens**.
5.  Click **Tokens (classic)**.
6.  Click **Generate new token (classic)**.
      * *Note: Select the `repo` scope to give it access to your repositories.*
7.  Copy the generated token (it will start with `ghp_` or similar).

#### **Step 2: Run the Command**

Replace `YOUR_GITHUB_PAT` in the command below with the token you just copied.

```bash
claude mcp add --transport http github https://api.githubcopilot.com/mcp -H "Authorization: Bearer YOUR_GITHUB_PAT" --scope project
```

**Example:**
If your token is `ghp_12345abcdef`, the command would look like this:
`claude mcp add github --transport http https://api.githubcopilot.com/mcp -H "Authorization: Bearer ghp_12345abcdef"`