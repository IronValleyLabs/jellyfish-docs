# Skills System

Skills are reusable procedures that agents create, save, and share with the entire team. When an agent discovers an effective workflow, it can save it as a skill so any agent can use it later.

## How Skills Work

```
Agent discovers a process that works
    ↓
Agent calls create_skill with name + instructions
    ↓
Skill saved to agent-created-skills.json
    ↓
All agents can now see and use the skill
    ↓
Skills appear in the Skills panel in the UI
```

## Skill Structure

Each skill has:

| Field | Description |
|-------|-------------|
| `name` | Short, descriptive name (e.g. "Instagram Post Workflow") |
| `description` | What the skill does (1-2 sentences) |
| `instructions` | Step-by-step instructions the agent follows |
| `agentId` | Which agent created it |
| `createdAt` | When it was created |

## Creating Skills

### Via Agent (Autonomous)
Agents create skills automatically when they discover repeatable processes:

```
Agent prompt: "create_skill"
Args: {
  "name": "Check ROAS",
  "description": "Check Return on Ad Spend from Meta Ads dashboard",
  "instructions": "1. Use computer_use to navigate to Meta Business Suite\n2. Go to Ads Manager > Overview\n3. Extract ROAS metric for last 7 days\n4. Compare with KPI target (ROAS > 2)\n5. Report findings via send_message"
}
```

### Via Chat
You can ask the agent directly:

> "Create a skill for generating weekly SEO reports. The skill should search for trending keywords, analyze top competitors, and create a markdown report with keyword data."

The agent will use `create_skill` to save it.

### Via Skills Panel
The Skills page shows all agent-created skills with options to view and delete.

## Skill Best Practices

### Good Skill
```
Name: "Weekly Competitor Analysis"
Instructions:
1. Use web_search to find top 5 competitors for [industry]
2. For each competitor, search for their recent content/campaigns
3. Create a spreadsheet comparing: features, pricing, content frequency
4. Create a document summarizing key findings and opportunities
5. Delegate content ideas to Content Manager
6. Send summary message to human
```

### Bad Skill
```
Name: "Do research"
Instructions: "Research things and make a report"
```

### Tips
- **Be specific:** Include exact steps, tool names, and expected outputs
- **Include tool references:** "Use `web_search` to find..." not just "Find..."
- **Add decision points:** "If ROAS < 2, alert the human via `send_message`"
- **Make them reusable:** Use placeholders like [industry], [competitor], [date range]
- **Chain tools:** Show the full workflow from research to deliverable

## Nano Jellys and Skills

Nano jellys can also create skills. When a nano discovers something useful during its subtask, it can save it for the team:

```
Nano receives task: "Research Instagram engagement tactics"
Nano executes: web_search → create_document → create_skill
Result: New skill "Instagram Engagement Tactics" available to all agents
```
