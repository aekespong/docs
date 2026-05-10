# From Local to Remote

## Built-in Tools

The simplest kind of tool lives directly inside the application. When the AI calls `get_current_time`, the app just runs a single line:

```
return new Date().toISOString();  // → "2026-05-07T10:32:00.000Z"
```

## Calling External APIs

A tool can do anything that returns a result — including calling an external API:

```
case 'get_weather':
  const data = await fetch(`https://weather-api.example.com/?city=${args.city}`);
  return `14°C — Partly cloudy in ${args.city}`;
```

The AI sees only the result string. It does not know or care how the data was fetched — whether it came from a calculation, a database, or a live API call across the internet.

## The Problem with Hardcoding

As you add more tools, the list grows — and so does the maintenance burden. Every new capability requires a code change and a redeployment. The tool definitions are written once and never change unless a developer touches the code.

This is the problem MCP solves.

## What MCP Adds

An MCP server is an external HTTP service that does two things:

1. **Advertises its tools** — responds to a discovery request with a full list of tool definitions
2. **Executes tool calls** — receives a tool name and arguments, runs the logic, and returns the result

Instead of hardcoding tools, the application asks the MCP server at runtime: *"what can you do?"* The server answers with definitions. The AI gets those definitions, calls the tools when needed, and the server handles execution.

**New tools added to the MCP server become available instantly — no redeployment of this app needed.**

## In This App

The **MCP Servers** panel on the right lets you paste the URL of any MCP server. The app contacts it, retrieves its tool list, and the AI can start using those tools immediately.

The pre-configured server in this demo is a real MCP endpoint. Its tools appear automatically alongside the built-in ones in the right sidebar.
