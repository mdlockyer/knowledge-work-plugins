# Slack Plugin

This repository contains the configuration needed to integrate Slack with Cursor IDE and Claude Code. The plugin enables your agents to interact directly with your Slack workspace, allowing you to search messages, send communications, manage canvases, and more—all through natural language.

## Features

This plugin provides the following capabilities:

- **Search**: Find messages, files, users, and channels (both public and private)
- **Messaging**: Send messages, retrieve channel histories, and access threaded conversations
- **Canvas**: Create and share formatted documents, export content as markdown
- **User Management**: Retrieve user profiles including custom fields and status information

## Prerequisites

- Cursor IDE or Claude Code CLI installed
- Access to a Slack workspace

## Installation

Choose the installation method for your IDE:

### Claude Code

If you're using Claude Code CLI, you can install this as a plugin by cloning it locally:

```bash
git clone https://github.com/slackapi/slack-mcp-plugin.git
cd slack-mcp-plugin
claude --plugin-dir ./
```

The Slack integration will be configured when the plugin loads. You will be prompted to authenticate via OAuth.

### Cursor

#### Step 1: Open Cursor Settings

Navigate to **Cursor → Settings → Cursor Settings** (or use the keyboard shortcut `Cmd+,` on macOS, `Ctrl+,` on Windows/Linux).

