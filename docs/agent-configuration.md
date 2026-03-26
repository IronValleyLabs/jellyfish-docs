# Agent Configuration Guide

This guide explains every field you can use to configure a Mini Jelly agent in Jellyfish.

## Configuration Fields

### Required Fields

#### `name`
The agent's display name. This is how it appears in the dashboard, chat, and Team Feed.

```
Social Media Manager
SEO Research Analyst
Customer Support Lead
```

#### `role`
The agent's job title. Used in its system prompt to define its identity.

```
Social Media Manager
Senior SEO Analyst
Lead Customer Support Specialist
```

#### `icon`
An emoji that identifies the agent visually. Max 4 characters.

```
🎨  (creative roles)
🔍  (research roles)
📊  (analytics roles)
💬  (support roles)
📧  (email/outreach roles)
```

### Optional Fields

#### `jobDescription`
A detailed paragraph describing what this agent does, its responsibilities, and its context. This becomes part of the agent's core identity.

**Good example:**
```
You are an expert SEO analyst. Your job is to research keywords, analyze
competitor rankings, find content gaps, track trending search topics, and
provide actionable SEO recommendations. You write detailed reports with
keyword data, search volume insights, and content strategy suggestions.
```

**Bad example:**
```
Do SEO stuff.
```

#### `goals`
Specific, actionable goals the agent should work toward. One goal per line. The agent reads these every planning cycle and plans actions to achieve them.

```
Research trending keywords weekly
Analyze competitor content and backlinks
Identify content gaps and opportunities
Create keyword research reports with data
Monitor search engine algorithm updates
```

**Tips:**
- Be specific: "Post 3 times per day" not "Post regularly"
- Make them measurable: "Respond within 5 minutes" not "Respond fast"
- Include frequency: "weekly", "daily", "every Monday"

#### `kpis`
Key Performance Indicators the agent is measured on. The agent will actively try to track and improve these metrics.

```
Keyword reports generated per week > 2
Content opportunities identified per report > 5
Engagement rate > 3%
Response time < 5 minutes
ROAS > 2.0
```

**How KPIs work:**
- The agent includes KPIs in its planning context
- It will use `web_search` and `computer_use` to check metrics
- It reports KPI progress in documents and messages
- KPIs influence what actions the agent prioritizes

#### `specMarkdown`
The most powerful field. A full Markdown document with detailed instructions, tone guidelines, constraints, workflows, and strategy. This is the agent's "brain" — the more detailed, the better it performs.

**Structure a good spec like this:**

```markdown
## Core Responsibilities
- What the agent should do daily/weekly
- Specific tasks and deliverables

## Tools Usage
- Which tools to use and when
- Specific workflows (e.g. "Use web_search first, then create_document")

## Content Strategy (if applicable)
- Tone and voice guidelines
- Content mix ratios
- Platform-specific rules

## Performance Standards
- Quality expectations
- Response time requirements
- Output format preferences

## Communication
- How to report to the human
- When to delegate vs. handle alone
- Language preferences
```

See [`../examples/`](../examples/) for complete spec examples.

#### `accessNotes`
Human-readable description of what the agent has access to. **Never put real passwords here** — use it for context.

```
Login: marketing@company.com (password in Settings)
Has access to: Google Analytics, Meta Business Suite, Metricool
API keys configured: OpenAI (for image generation)
No access to: Bank accounts, HR systems
```

#### `skills`
Array of skill IDs the agent can use. If empty, the agent has access to all implemented skills. You can restrict agents to specific capabilities.

```json
["websearch", "draft", "generate_image", "browser_visit"]
```

#### `computerUseEnabled`
When `true`, the agent can control a real browser (Chrome) to interact with websites, dashboards, and web apps.

#### `computerUseAutonomous`
When `true`, the agent can use the browser without asking for permission first.

#### `wakeOnSignals`
When `true` (default), the agent is activated when the engine starts or when "trigger all" is used. Set to `false` for agents that should only respond to direct messages.

## Agent Lifecycle

```
1. CREATED    → Agent configuration saved to team.json
2. PLANNING   → Agent reads spec, goals, KPIs, pending tasks
3. EXECUTING  → Agent runs tools (web search, create files, etc.)
4. SLEEPING   → Agent waits before next planning cycle
5. REPLANNING → Back to step 2
```

Each planning cycle, the agent:
- Checks for human requests (top priority)
- Checks for delegated tasks from other agents
- Reviews its goals and KPIs
- Plans up to 5 actions
- Executes them with real tools
- Reports results

## Language

Agents automatically match the user's language. If you configure goals and specs in Spanish, the agent will work and report in Spanish. If in English, it responds in English.
