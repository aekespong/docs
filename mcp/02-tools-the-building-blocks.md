# Tools — The Building Blocks

## What Is a MCP Tool?

In MCP, a **tool** is a named capability that the AI can call. Each tool is described in plain language — not as code, but as a short specification that the AI can read and understand.

Every tool has three parts:

- **Name** — a unique identifier, such as `get_current_time`
- **Description** — a plain-English sentence explaining what it does and when to use it
- **Parameters** — the inputs the tool expects, each with a name, type, and description

## An Example

Here is how the two built-in tools in this app are described to the AI:

**get_current_time**
> Returns the current UTC date and time as an ISO 8601 string.
> *(No parameters needed.)*

**get_weather**
> Returns the weather for a location.
> Parameters: `city`

## The Key Insight

The AI never sees the *implementation* of a tool — only its description. This means:

- The AI decides **whether** and **when** to call a tool based purely on the description
- You can change what a tool does internally without the AI noticing
- You can dynamically add servers and gain functionality without modifying the code

**The description is the contract.** Write it clearly, and the AI will use the tool correctly. A vague description leads to the AI calling the tool at the wrong time — or not at all.

## Tools in This App

Open the **MCP Servers** panel on the right to see the full list of available tools and their descriptions. Built-in tools are always present; Add MCP servers and load there description and test them out.
