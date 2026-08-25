# TopicLift Editorial Copilot for Claude Code

TopicLift Editorial Copilot connects Claude Code to the TopicLift remote MCP server. It provides read-only access to authorized TopicLift sites for traffic analysis, Google Search, Google Discover, Google News, aggregate search queries and evidence-backed publication recommendations.

The plugin uses TopicLift OAuth by default. It does not contain a TopicLift token or any other secret.

## Install for local testing

From a Claude Code session, load the plugin directory directly:

```text
claude --plugin-dir ./plugins/topiclift-claude
```

Then authenticate the MCP connection from the Claude Code session:

```text
/mcp
```

Select `topiclift` and complete the TopicLift read-only authorization in the browser. On supported Claude Code versions, the equivalent command is:

```text
claude mcp login topiclift
```

## Manual token alternative

For a local or test configuration where OAuth is not desired, create a personal read-only token in TopicLift Settings and configure a separate user-scoped server. Keep the token in an environment variable and never commit it:

```text
export TOPICLIFT_ACCESS_TOKEN="paste-the-token-in-your-local-shell-only"
claude mcp add-json topiclift-token '{"type":"http","url":"https://topiclift.io/mcp","headers":{"Authorization":"Bearer ${TOPICLIFT_ACCESS_TOKEN}"}}' --scope user
```

Do not configure a static Authorization header on the OAuth-based `topiclift` entry: Claude Code will not fall back to OAuth if that header is rejected.

## What the skill does

The bundled `editorial-copilot` skill tells Claude when and how to use TopicLift tools, how to keep an analysis scoped to one site, and how to present metrics, supporting articles, confidence and editorial recommendations without inventing facts.

The MCP server remains authoritative for live data, permissions, scopes and read-only enforcement.

## Claude.ai

This package targets Claude Code. In Claude.ai, connect the same remote MCP server through the Claude MCP connector and complete the TopicLift OAuth flow. The endpoint is:

```text
https://topiclift.io/mcp
```

## Security

- TopicLift access is read-only.
- OAuth and personal tokens are user-specific and revocable.
- Never paste a token into a conversation or commit it to a repository.
- Do not use this integration to publish or modify WordPress content.
