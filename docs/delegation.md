# Agent Delegation & Communication

Jellyfish agents can communicate with each other and delegate tasks, enabling true team collaboration.

## How Delegation Works

```
SEO Analyst finds trending keywords
    ↓
SEO Analyst calls: delegate({
  to: "Social Media Manager",
  task: "Create 3 posts based on these keywords: AI tools, remote work, sustainability"
})
    ↓
Task saved to delegation queue (SQLite)
    ↓
Social Media Manager's next planning cycle:
  "🔔 PENDING TASK from @SEO Research Analyst:
   Create 3 posts based on these keywords..."
    ↓
Social Media Manager plans actions for this task (PRIORITY)
    ↓
Social Media Manager executes and reports back
```

## Delegation Queue

- Delegated tasks are stored in a SQLite database (`agent_delegations` table)
- Each delegation has: `from_agent`, `to_agent`, `task`, `status`, `response`
- Status flow: `pending` → `completed`
- Pending delegations appear as **top priority** in the target agent's planning prompt

## Message Types

### Human → Agent
When you type in the chat, your message is forwarded to the relevant agent(s). Human requests are marked as **TOP PRIORITY** (above delegations).

```
💬 Human said (2:30 PM): "Create a report on our SEO performance this month"
```

### Agent → Human
Agents use `send_message` to communicate with the human:

```json
{ "message": "Weekly SEO report is ready. Key findings: organic traffic up 15%, 3 new keyword opportunities identified." }
```

### Agent → Agent
Agents delegate via the `delegate` tool:

```json
{
  "to": "Content Manager",
  "task": "Write a blog post about 'Top 10 AI Tools for Small Business' based on my keyword research. Target 1500 words, include H2/H3 headers, and optimize for the keyword 'AI tools for business'."
}
```

## Priority Order

When an agent plans its next actions, it considers tasks in this order:

1. **Human requests** (highest priority) — Direct messages from the user
2. **Pending delegations** — Tasks from other agents
3. **Goals & KPIs** — The agent's own objectives
4. **Autonomous planning** — Proactive work based on role

## Multi-Agent Team Examples

### Marketing Team
```
SEO Analyst ──→ finds keywords ──→ delegates to Content Manager
Content Manager ──→ writes blog post ──→ delegates to Social Media Manager
Social Media Manager ──→ creates social posts from blog content
```

### Support Team
```
Customer Support ──→ identifies common issue ──→ delegates to DevOps
DevOps ──→ investigates and fixes ──→ reports back to Support
Customer Support ──→ updates customer
```

### Research Team
```
Market Researcher ──→ competitor analysis ──→ delegates to Data Analyst
Data Analyst ──→ creates spreadsheet with data ──→ delegates to BI Analyst
BI Analyst ──→ creates dashboard report
```

## Best Practices

1. **Be specific in delegations:** Include all context the target agent needs
2. **Use agent names:** The delegate tool matches by name (fuzzy matching works)
3. **Don't over-delegate:** Each agent should do its own core work
4. **Chain delegations:** Agent A → Agent B → Agent C for complex workflows
5. **Include data:** When delegating, include relevant findings or file references
