 # Costs of MCP
 
 MCP tool calls are inherently expensive. 
 
 Here's why:

  Where the tokens go in a single MCP interaction:

  1. System/tool definitions — Every request sends the full JSON schema for every available tool. If you have 10-20 MCP tools with descriptions and parameter schemas, that alone can be 2–5k
  tokens per request.
  2. Conversation history — The full conversationHistory array is sent every turn. After a few exchanges it grows fast.
  3. Tool call round-trips — Each iteration of the loop costs tokens:
    - Request → model reasons, calls a tool (~500–1k)
    - Tool result injected into messages (~500–5k depending on MCP response size)
    - Model reads the result and responds again
  4. MCP responses are verbose — Ardoq in particular returns large JSON payloads. The tool result gets added to the messages array and sent back in the next iteration.

  Rough breakdown for a simple Ardoq question:
  - Tool schemas: ~3–4k
  - Conversation: ~1k
  - Tool call + response JSON: ~5–8k
  - Model output: ~1–2k

  Ways to reduce it:

  - Summarize/truncate MCP results before adding to context — big JSON responses often have far more data than the model needs
  - Limit tools sent per request — only send tools relevant to the conversation
  - Trim conversation history — only keep last N turns instead of everything
  - Use a smaller model for tool calls and a larger one for the final answer

  14k for an MCP query is actually fairly typical, not a sign anything is broken. Want me to implement any of the reduction strategies?