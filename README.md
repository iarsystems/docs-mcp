# IAR Documentation MCP Server

The IAR Documentation MCP Server gives AI assistants access to the official IAR documentation published on [docs.iar.com](https://docs.iar.com), enabling more accurate answers about compiler options, pragmas, linker configuration, project settings, debugging, probes, and related topics.

## Why use it?

Instead of searching documentation manually, you can ask your AI assistant questions in natural language and get answers grounded in the same documentation available on docs.iar.com, often with links to the original source material.

Example questions:

- What does diagnostic Pe188 mean?
- How does `#pragma location` work in EWARM?
- How do I configure a debug probe for my target?

---

## Endpoint

[Connect to the IAR Documentation MCP Server](https://docs-mcp.iar.com/mcp)

---

## Installation

### Claude Code

Add the server for the current project:

```bash
claude mcp add --transport http iar-docs https://docs-mcp.iar.com/mcp
```

Add `-s user` to make it available across all projects:

```bash
claude mcp add -s user --transport http iar-docs https://docs-mcp.iar.com/mcp
```

Verify the connection:

```bash
/mcp
```

You should see `iar-docs` listed as connected.

### Visual Studio Code (GitHub Copilot Agent Mode)

Create or edit `.vscode/mcp.json`:

```json
{
  "servers": {
    "iar-docs": {
      "type": "http",
      "url": "https://docs-mcp.iar.com/mcp"
    }
  }
}
```

### Cursor

Create or edit `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "iar-docs": {
      "url": "https://docs-mcp.iar.com/mcp"
    }
  }
}
```

### Claude Desktop / Claude.ai

If your plan supports custom MCP connectors:

1. Open **Settings**
2. Go to **Connectors**
3. Select **Add Custom Connector**
4. Enter:

```text
https://docs-mcp.iar.com/mcp
```

### Other MCP Clients

The IAR Documentation MCP Server implements the standard MCP protocol and can be used with other MCP-compatible AI clients.

**Endpoint:** https://docs-mcp.iar.com/mcp

Refer to your client's documentation for MCP server configuration instructions.



## Usage

Once connected, simply ask questions about IAR products in natural language.

For best results:

- Specify the IAR product and version (EWARM, EWRISCV, EWRX, EWRH850, EWRL78, etc.).
- Mention the target architecture when relevant.
- Include the exact compiler option, pragma, linker directive, or diagnostic number when available.
- Include error messages verbatim when troubleshooting build or linker issues.

The AI assistant automatically uses the MCP server when documentation lookup is needed. No special commands or manual tool invocation are required.

---

## Documentation Coverage

At the creation of the MCP server, the documentation corpus included these products. 
Documentation coverage will continue to expand over time, with future product releases.

- IAR Embedded Workbench for Arm (EWARM) 10.10
- IAR Embedded Workbench for RISC-V (EWRISCV) 3.40
- IAR Embedded Workbench for RH850 (EWRH850) 3.20
- IAR Embedded Workbench for RL78 (EWRL78) 5.20
- IAR Embedded Workbench for RX (EWRX) 5.20
- IAR debug probes documentation
- IAR Library and Migration Support documentation (LMSC)
- IAR Orbit 6.40
- IAR Secure Deploy Platform (SDP) 6.40

---

## Notes

- Documentation content is sourced from the documentation available on [docs.iar.com](https://docs.iar.com).
- No authentication is currently required.
- Requests may be rate limited to ensure service availability.
- Answers may include links to relevant documentation pages for further reading.

---

## Feedback

Feedback, bug reports, and requests for additional documentation coverage are welcome.
