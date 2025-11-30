# n8n_workflows
#🐞 AI-Powered GitHub Debugger Agent

An automated code quality agent that fetches your code, detects bugs using LLMs, and fixes them—but only when you say so.

#📖 Overview

The AI-Powered GitHub Debugger Agent is an n8n workflow designed to act as a "Human-in-the-Loop" DevOps bot. It autonomously audits your repository for bugs, inefficiencies, and redundancy.

Instead of blindly committing AI-generated code, it sends a detailed report to Discord. You review the changes, and if you approve (via a secure webhook link), the agent pushes the fixes directly to your repository.

#✨ Key Features

📂 Auto-Fetch: Recursively scans your GitHub repository for code files (.js, .ts, .py, .cpp, etc.).

🧠 Intelligent Analysis: Uses GPT-4o to identify logic errors, O(n²) inefficiencies, and redundant variables.

🛡️ Human-in-the-Loop: Zero code is committed without your explicit click of an approval link.

🔔 Real-time Reporting: Delivers formatted Markdown bug reports directly to your Discord server.

⚡ Automated Fixes: Applies the AI-suggested refactor instantly upon approval.

#🏗️ Architecture

The workflow operates in a linear 4-phase loop:

Ingestion: Fetches the file tree from GitHub and filters for source code.

Analysis: The LLM reads the code and outputs a JSON object containing a Documentation report and Fixed_Code.

Authorization: The workflow pauses and sends a webhook link to Discord.

Execution: Once the link is clicked, the workflow resumes and commits the changes via the GitHub API.

#🚀 Getting Started

Prerequisites

n8n Instance: Self-hosted or Cloud (v1.0+).

GitHub Account: A Personal Access Token (Classic) with repo scope.

OpenAI API Key: Access to GPT-4o or GPT-3.5-Turbo.

Discord Server: Ability to create Webhooks.

Installation

Import the Workflow:

Copy the JSON workflow code (located in workflow.json or provided separately).

In n8n, go to Workflows > Import from JSON.

Configure Credentials:

GitHub API: Create a credential in n8n using your Personal Access Token.

OpenAI API: Create a credential using your API Key.

Setup Nodes:

Manual Trigger: Set your default Owner, Repo, and Branch.

Send to Discord: Paste your Discord Webhook URL.

Filter Code Files: (Optional) Add extensions like .rs or .go if needed.

#🕹️ Usage

Trigger the Agent:

Open the workflow in n8n and click "Execute Workflow" (or use the Manual Trigger form).

Wait for Analysis:

The agent will process files in batches.

Check Discord:

You will receive a notification: "🐞 Bug Report for src/app.js".

Approve or Ignore:

To Fix: Click the "Approve & Commit" link in the message.

To Skip: Simply ignore the message. The workflow will not modify the file.

#🔮 Roadmap

We are constantly improving the agent. Here is what's coming in v2.0:

[ ] Pull Request Integration: Create a fix/ai-branch and open a PR instead of committing directly to main.

[ ] RAG (Context-Awareness): Use a vector store (Pinecone) so the AI understands cross-file dependencies.

[ ] Local LLM Support: Option to swap OpenAI for Ollama/Llama 3 for data privacy.

[ ] Compiler Loop: Run a build command (e.g., npm test) to verify the fix before asking for human approval.

#📄 License

Distributed under the MIT License. See LICENSE for more information.

<p align="center">
Built with ❤️ using <a href="https://n8n.io">n8n</a> and ☕
</p>
