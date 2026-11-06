# HotCodePush MCP Server

The official MCP server for [HotCodePush](https://hotcodepush.com), the over-the-air (OTA) update service for React Native, Expo, Capacitor and Cordova. It lets AI agents release, roll out, pause and roll back OTA updates, manage apps and channels, read update statistics and search the docs. Every tool does exactly what the signed-in person may do.

## Endpoint

The server is hosted and ready to use:

```text
https://mcp.hotcodepush.com/mcp
```

It speaks the streamable HTTP transport of the [Model Context Protocol](https://modelcontextprotocol.io). The setups below sign in through OAuth. The docs tools need no sign-in: add `?toolsets=docs` to the URL.

Uploading a bundle stays with the [CLI](https://hotcodepush.com/docs/cli). The server releases what was uploaded.

## Installation

### ChatGPT

ChatGPT connects a custom MCP server on a Business, Enterprise or Edu workspace, and on Pro for reads alone. Open [Plugins](https://chatgpt.com/plugins), select the plus button, then Add custom MCP server. Enter the name `HotCodePush` and the URL, choose OAuth as the authentication and select Create as a plugin. Install the plugin, then type `@` in a new conversation and pick it.

### Claude Code

Run this in the project, or with `--scope user` for every project:

```sh
claude mcp add --transport http hotcodepush "https://mcp.hotcodepush.com/mcp"
```

Then run `/mcp` in Claude Code and choose `hotcodepush` to sign in.

### Claude Desktop

Open Customize › Connectors › Add custom connector. Enter the name `HotCodePush` and the URL and connect. The same connector works on claude.ai.

### Codex

Add the server to `~/.codex/config.toml`:

```toml
[mcp_servers.hotcodepush]
url = "https://mcp.hotcodepush.com/mcp"
```

Then run `codex mcp login hotcodepush`.

### Cursor

Add `.cursor/mcp.json` to your project, or `~/.cursor/mcp.json` for every project:

```json
{
  "mcpServers": {
    "hotcodepush": {
      "url": "https://mcp.hotcodepush.com/mcp"
    }
  }
}
```

### VS Code

Add `.vscode/mcp.json` to your project:

```json
{
  "servers": {
    "hotcodepush": {
      "type": "http",
      "url": "https://mcp.hotcodepush.com/mcp"
    }
  }
}
```

Each client opens the consent page in your browser once. API tokens for headless clients, toolsets, read-only mode and other clients are covered in the [docs](https://hotcodepush.com/docs/ai/mcp).

## Usage

Ask your agent, for example:

- "Which channels does my app have?"
- "Pause the current release in the production channel."
- "How many devices applied updates in the last seven days?"

## Documentation

- [MCP server](https://hotcodepush.com/docs/ai/mcp): sign-in, client setup, toolsets and troubleshooting.
- [Tools](https://hotcodepush.com/docs/ai/mcp/tools): every tool by toolset.

## License

MIT. See [LICENSE](LICENSE).
