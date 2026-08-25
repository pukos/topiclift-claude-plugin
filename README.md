# TopicLift Editorial Copilot

Claude Code plugin and marketplace entry for TopicLift.

TopicLift Editorial Copilot connects Claude Code to the TopicLift remote MCP server for read-only editorial intelligence:

- traffic for published editorial content;
- Google Search, Discover and Google News performance;
- aggregate Search Console queries;
- evidence-backed publication recommendations.

The plugin uses OAuth and does not contain TopicLift credentials or other secrets.

## Install from this marketplace

Add this repository as a Claude Code marketplace, then install `topiclift-editorial-copilot`.

For local development:

```text
claude --plugin-dir ./plugins/topiclift-claude
```

After the plugin loads, use `/mcp` to connect TopicLift and complete the read-only OAuth authorization in the browser.

## Links

- [TopicLift](https://topiclift.io)
- [Privacy policy](https://topiclift.io/privacy)
- [Terms](https://topiclift.io/terms)
- [Plugin documentation](./plugins/topiclift-claude/README.md)
