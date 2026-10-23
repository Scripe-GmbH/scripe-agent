<p align="center">
  <img src="assets/logo.svg" alt="Scripe" width="96" />
</p>

<h1 align="center">Scripe for AI agents</h1>

<p align="center">
  Plan, write, schedule and measure your team's LinkedIn posts in
  <a href="https://scripe.io">Scripe</a> from Hermes Agent, Claude, ChatGPT,
  Codex, Cursor, Gemini CLI and any other agent that speaks MCP.
</p>

Scripe is a social media management platform for B2B teams and agencies,
built LinkedIn-first. This repository packages Scripe for agents:

- **`skills/scripe/SKILL.md`**, an [Agent Skill](https://agentskills.io) that
  teaches an agent how to work with Scripe: plan a period for every profile,
  write posts in each person's voice, schedule, publish and read analytics.
- **The hosted Scripe MCP server**, `https://mcp.scripe.io/mcp`. Nothing to
  install or run: sign in with OAuth on first use. ~130 operations across
  posts, ideas, the calendar, the knowledge base, media, analytics and brand
  settings.
- **Plugin manifests** for Claude Code, Cursor, Grok Build and Gemini CLI that
  bundle the two.

You need a Scripe account. Every plan, Free included, can connect;
scheduling and publishing need a paid plan or a trial.
[Start free](https://scripe.io).

## Install

### Hermes Agent

```bash
hermes skills install well-known:https://scripe.io/.well-known/skills/scripe
```

Then connect the MCP server in `~/.hermes/config.yaml`:

```yaml
mcp_servers:
  scripe:
    url: "https://mcp.scripe.io/mcp"
    auth: oauth
```

```bash
hermes mcp login scripe
```

### Claude Code

```text
/plugin marketplace add Scripe-GmbH/scripe-agent
/plugin install scripe@scripe-agent
```

### Gemini CLI

```bash
gemini extensions install https://github.com/Scripe-GmbH/scripe-agent
```

### Any skills-compatible agent (Codex, Cursor, OpenClaw, …)

```bash
npx skills add Scripe-GmbH/scripe-agent
```

and add `https://mcp.scripe.io/mcp` as a remote MCP server in that agent.

### Claude, ChatGPT and other MCP clients

Add a custom connector with the URL `https://mcp.scripe.io/mcp`.

Setup for every host: [skills/scripe/references/connect.md](skills/scripe/references/connect.md).

## Try it

- "Plan next week's LinkedIn posts for everyone on the team."
- "Write a LinkedIn post in my voice about what we learned this quarter."
- "Turn yesterday's customer call into three post ideas."
- "How did my posts perform last month, and which formats worked?"
- "Schedule the draft about pricing for Tuesday 9:00."

## What it will not do

Publishing a post right away, deleting anything and sending a review request
each ask for your confirmation first. Scripe never likes, comments on or
reposts other people's LinkedIn posts for you.

## Network and credentials

This package contains no code, hooks, scripts or binaries: only Markdown and
JSON manifests. It connects one network endpoint, the hosted MCP server
`https://mcp.scripe.io/mcp`, whose OAuth authorization server is
`https://scripe.io`. No API key, token or environment variable is needed or
read: the host signs in with OAuth 2.1 (Dynamic Client Registration + PKCE)
and stores the token itself.

## Links

- MCP docs: https://scripe.io/developers/api/v1/mcp
- Tool catalog: https://scripe.io/developers/api/v1/mcp-catalog
- Status: https://status.scripe.io
- Privacy: https://scripe.io/privacy · Terms: https://scripe.io/terms
- Support: hello@scripe.io

This repository is published from Scripe's main codebase; open an issue here
or write to hello@scripe.io.
