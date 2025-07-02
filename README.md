# 🧠 Copilot Agent Mode + MCP Quest

**Estimated Time:** \~60 minutes
**Level:** Intermediate
**Prerequisite Quest:** _Build a High School Quiz App Using Copilot Agent Mode_

---

## 🏫 Scenario Recap

Great job building the Quiz App! 🎉
But here's the catch: they're all submitting bug reports, feature requests, and ideas at once... and it's overwhelming. 😱

The good news? We can scale our response by augmenting **GitHub Copilot** with the **GitHub MCP Server** and supercharging our workflow using **Agent Mode**.

Let’s turn GitHub Copilot into a smart teammate that can triage issues, research enhancements, and even generate code — all from within your Codespace.

---

## 🎯 Learning Objectives

By the end of this quest, you will:

- Set up and configure the GitHub MCP Server in your Codespace
- Use Copilot Agent Mode + MCP to research similar projects and generate ideas
- Automatically create and triage GitHub issues
- Implement, commit, and review a solution — all via Copilot
- Learn to responsibly validate and merge AI-generated code

---

## 🔄 Quest Stages

### ✅ Step 1: Introduction to MCP + Environment Setup

**Goal:** Configure the MCP server to expand Copilot’s powers.
🧠 _MCP = "USB-C for AI"_
It helps AI tools like Copilot understand what external tools (like GitHub) are capable of and how to interact with them safely.

**⌨️ Activity:**

1. Open your Quiz App repository in a GitHub Codespace
2. Confirm extensions:

   - GitHub Copilot Chat ✅
   - Python ✅

3. Verify the app works:

   - Go to the **Run and Debug** tab
   - Click ▶️ **Start Debugging**
   - Preview the app in the **Ports** tab

**🧠 Add the MCP Server:**
Create `.vscode/mcp.json` and add:

```json
{
  "servers": {
    "github": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "ghcr.io/github/github-mcp-server:v0.1.1"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}"
      }
    }
  },
  "inputs": [
    {
      "type": "promptString",
      "id": "github_token",
      "description": "GitHub Personal Access Token",
      "password": true
    }
  ]
}
```

**🪪 Grab your token by running:**

```bash
echo $GITHUB_TOKEN
```

- Use it when prompted to start the server.
- Commit and push `.vscode/mcp.json` (just for this exercise).
  🎉 _Now, Copilot can talk to GitHub via MCP!_

---

### 🤖 Step 2: Agent Mode + MCP in Action

**Goal:** Use Copilot’s new powers to research similar projects and generate ideas.

**⌨️ Activity:**

1. Close any open files

2. Ensure Agent Mode is enabled and MCP tool is active

3. Ask Copilot:

   - `"Are there any GitHub repositories that help schools organize extracurricular activities?"`

4. When prompted to use MCP, approve the request. Then ask:

   - `"Please describe the third result in detail — what are its core features?"`
   - `"Compare its features with ours. Which are new to us?"`
   - `"Let’s create GitHub issues for these new ideas."`

✅ Copilot will ask permission to open issues — approve as needed.
💡 _Tip: Click the ➕ “New Chat” icon after finishing this conversation to reset context._

---

### 🧰 Step 3: Solve Issues with Agent Mode

**Goal:** Select and implement one of the auto-generated GitHub issues.

**⌨️ Activity:**

1. Ask Copilot:

   - `#codebase How many open issues are there?`

2. Then:

   - `"Please get the list of issues, review the descriptions, and pick the top 3 most important."`

3. Choose one and say:

   ```text
   #codebase Let’s do the first one. Follow these steps:

   Create a new branch
   Implement the fix or feature
   Push changes and open a pull request.
   ```

⚠️ Always review Copilot’s proposed commands and code — MCP gives Copilot real power.
Mona will automatically detect your PR and begin reviewing.

---

### ✅ Step 4: Validate and Merge AI-Generated Code

**Goal:** Responsibly review Copilot’s work and finalize your implementation.

**⌨️ Activity:**

1. Open the pull request in GitHub
2. Review the code and confirm it matches the original issue
3. Merge the pull request

🎁 _Bonus:_ If you have Copilot-powered PR review, use it here.

Back in Copilot Chat, ask:

- `"Add a closing comment to the issue we just finished. Provide a 1-sentence summary of the fix and thank the commenters."`

🎉 Mona will again respond once the issue is closed.

---

## 🚀 Quest Complete!

You’ve now:

- ✅ Installed and configured a GitHub MCP Server
- ✅ Used Copilot Agent Mode + MCP to research projects and enhance your app
- ✅ Created issues and implemented a fix via Copilot
- ✅ Reviewed and merged AI-generated code safely
