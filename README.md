# Jellyfish - AI Agent Platform

<p align="center">
  <img src="assets/jellyfish-logo.png" alt="Jellyfish" width="120" />
</p>

**Jellyfish** is a desktop platform that lets you create, configure, and run autonomous AI agents (called **Mini Jellys**) that work together as a team. Each agent has a specific role, goals, KPIs, and real tools — they can search the web, create documents, generate images, write code, browse websites, delegate tasks to each other, and learn new skills.

This repository contains **public documentation, templates, and guides** for building effective agents on Jellyfish.

## What's Inside

| Path | Description |
|------|-------------|
| [`docs/agent-configuration.md`](docs/agent-configuration.md) | How to configure an agent (all fields explained) |
| [`docs/tools-reference.md`](docs/tools-reference.md) | Complete reference of the 12 tools agents can use |
| [`docs/skills-system.md`](docs/skills-system.md) | How agents create, share, and use skills |
| [`docs/delegation.md`](docs/delegation.md) | How agents communicate and delegate tasks |
| [`docs/nano-jellys.md`](docs/nano-jellys.md) | How nano jellys (mini-workers) work |
| [`docs/best-practices.md`](docs/best-practices.md) | Writing effective agent specs |
| [`docs/mcp-connectors.md`](docs/mcp-connectors.md) | 20 MCP connectors: ads, analytics, finance, logistics |
| [`docs/changelog.md`](docs/changelog.md) | Version history and release notes |
| [`templates/`](templates/) | Ready-to-use agent templates (20+) |
| [`examples/`](examples/) | Example agent specs and skill definitions |

## Quick Start

1. **Download Jellyfish** from [jellyfish.ai](https://jellyfish.ai) (Mac, Windows & Linux)
2. **Add your API key** (OpenAI, Google Gemini, or OpenRouter) in Settings
3. **Create your first agent** from a template or custom
4. **Start the engine** and watch your team work

## How Agents Work

```
Human creates agent with:
  - Role & job description
  - Goals & KPIs
  - Agent spec (detailed instructions)

Agent Engine starts:
  1. Agent reads its spec + goals + KPIs
  2. Plans actions (max 5 per cycle)
  3. Executes using real tools
  4. Reports results to Team Feed
  5. Sleeps, then replans

Agents can:
  - Delegate tasks to each other
  - Create reusable skills
  - Spawn nano jellys for parallel subtasks
  - Learn from what works and save it
```

## Agent Configuration

Each agent has these configurable fields:

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Agent's display name |
| `role` | Yes | Job title (e.g. "SEO Analyst") |
| `icon` | Yes | Emoji icon |
| `jobDescription` | No | Detailed job context |
| `goals` | No | What the agent should achieve (one per line) |
| `kpis` | No | Measurable targets (e.g. "ROAS > 2") |
| `specMarkdown` | No | Detailed instructions in Markdown |
| `accessNotes` | No | What the agent has access to |
| `skills` | No | Specific skill IDs to enable |

See [`docs/agent-configuration.md`](docs/agent-configuration.md) for the complete guide.

## Available Tools

Agents have access to 12 real tools:

| Tool | What it does |
|------|-------------|
| `web_search` | Search the web via DuckDuckGo |
| `computer_use` | Control a real browser (click, type, navigate) |
| `create_document` | Create markdown/HTML documents |
| `create_spreadsheet` | Create CSV data tables |
| `generate_image` | Generate images with DALL-E |
| `send_message` | Message humans or other agents |
| `file_operation` | Read, write, list, move, copy, delete files |
| `run_command` | Execute terminal/bash commands |
| `send_email` | Send emails via SMTP |
| `delegate` | Assign tasks to teammate agents |
| `create_skill` | Save a reusable skill for all agents |
| `spawn_nano` | Launch a nano jelly mini-worker |

See [`docs/tools-reference.md`](docs/tools-reference.md) for detailed usage.

## Templates

We provide 20+ ready-to-use templates across 5 categories:

- **Marketing & Sales** — Social Media Manager, Paid Media Manager, Content Manager, Email Marketing
- **Support & Operations** — Customer Support, Sales Rep, Logistics, DevOps
- **Data & Analytics** — Data Analyst, Market Researcher, QA Tester, BI Analyst
- **Finance & Admin** — Bookkeeper, HR Coordinator, Invoicing, Executive Assistant
- **Creative & Production** — Graphic Designer, Video Producer, Photo Editor, Audio Producer

Browse all templates in [`templates/`](templates/).

## Community

- [Discord](https://discord.gg/jellyfish) — Ask questions, share agent configs
- [Twitter](https://twitter.com/jellyfishai) — Updates and tips

## License

Documentation and templates are licensed under [CC BY 4.0](LICENSE). You're free to use, share, and adapt them.

---

Built with love by [Iron Valley Labs](https://github.com/IronValleyLabs)
