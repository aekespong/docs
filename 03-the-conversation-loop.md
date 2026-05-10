# The Conversation Loop

## Normal Chat vs Tool-Assisted Chat

In a plain conversation, the flow is simple:

> **You** → AI → **Answer**

When tools are involved, the AI goes through an extra step before answering:

> **You** → AI *(decides to call a tool)* → Tool runs → AI *(formulates answer)* → **Answer**

This two-step cycle is the heart of how MCP works in practice.

## Step by Step

### 1. You send a message
Your question arrives at the AI alongside a list of all available tools. The AI reads both.

### 2. The AI analyses your request
The AI decides: *can I answer this from what I already know, or do I need a tool?*

If a tool is needed, it responds not with an answer but with a **tool call** — a structured decision naming which tool to use and with what arguments.

> You can see this first response in the **AI analysis** section that appears above the tool results in this chat.

### 3. The tool runs
The application executes the requested tool and gets back a result — a timestamp, a number, a JSON payload, anything. In this educational app you can show the result in its raw format.

### 4. The AI answers
The tool result is handed back to the AI, which now has everything it needs. It produces a final, natural-language answer.

## Why Two Steps?

The AI cannot *run* code directly. It can only *describe* what it wants to happen. The application is the one that actually executes the tool and returns the result. This separation keeps the AI model clean and predictable — it reasons, the application acts.

## What You See in This App

When a tool is called, three things appear in the chat in sequence:

| What you see | What it is |
|---|---|
| **AI analysis** *(collapsible)* | The AI's reasoning from step 2 — how it decided which tool to call |
| **exec tool_name(args)** | The tool call and result from step 3 |
| **The assistant message** | The final answer from step 4 |

If no tool was needed, only the assistant message appears.
