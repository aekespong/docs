# Try It Yourself

## Built-in Tools

This app comes with two tools you can test right now, without any extra configuration.

### Get the current time

Try sending any of these:

- *"What time is it?"*
- *"What is today's date?"*
- *"Vad är klockan i Stockholm?"*

The last one is Swedish — the AI is multilingual and will reply in whatever language you write in. The tool returns a raw UTC timestamp, and the AI formats it naturally for your language and sometime adjusts the hours to match Stockolm CET. 

### Get the weather

Try sending:

- *"What is the weather in Stockholm"*

## What to Look For

After you send a message that triggers a tool, watch the chat for three things:

**AI analysis** — a collapsible section that appears first, showing the AI's reasoning before it calls any tool. Expand it to see how the model decided what to do and why.

**exec tool_name(args → result)** — the tool that was called, with its arguments. If the result was a JSON object, it appears as a collapsible block you can expand.

**The assistant message** — the final answer, incorporating the tool result.

If the AI answers from its training data instead of calling a tool, try being more explicit:
> *"Show a list of applications in a table and analyze if and when they will be retired."*

An advanced model will be able to respond to that and smaller models won't.

## MCP Servers

Open the **MCP Servers** panel on the right to explore further:

- **Active Servers** — the pre-configured server and any you have added
- **API Tokens** — authentication tokens for servers that require them
- **Available Tools** — the full list of tools the AI can currently use, with descriptions

To add an external MCP server, click **+ Add server** and paste its URL. Its tools will appear in the list immediately and the AI can use them in your next message. Some servers requires an API KEY for protecting sensitive data. 

## Going Further

The tools in this demo are simple by design. In a real deployment, MCP tools can search documents, query databases, create records, or call any API your organisation provides. The AI's behaviour scales with the tools you give it — the conversation loop stays exactly the same.

## List of other MCPs to try

Try: https://llmse.ai/mcp
Prompt: use tool to analyze solita.fi for AEO 

Find more MCP Servers on this site: https://registry.modelcontextprotocol.io/

