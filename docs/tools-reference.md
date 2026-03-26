# Tools Reference

Every Jellyfish agent has access to 12 real tools. These are not simulated — they perform actual operations on your system.

## 1. `web_search`

Search the web for real-time information using DuckDuckGo.

**Args:**
```json
{ "query": "search terms here" }
```

**Use for:**
- Current news, prices, trends
- Competitor research
- Keyword data
- Any information the agent doesn't have

**Example:** An SEO agent searching for trending keywords:
```json
{ "query": "trending SEO keywords March 2026" }
```

---

## 2. `computer_use`

Open a real Chrome browser and interact with websites — click buttons, fill forms, take screenshots, extract data.

**Args:**
```json
{
  "url": "https://example.com",
  "goal": "Log in and extract the engagement metrics from the dashboard"
}
```

**Use for:**
- Accessing dashboards (Analytics, Metricool, Meta Business Suite)
- Social media interactions
- Web scraping with visual context
- Any task requiring a real browser

**Requirements:** `computerUseEnabled: true` in agent config.

---

## 3. `create_document`

Create a document (Markdown or HTML) and save it to the outputs directory.

**Args:**
```json
{
  "title": "Weekly SEO Report",
  "content": "## Summary\n\nThis week's keyword analysis shows...",
  "format": "md"
}
```

**Formats:** `md` (default), `html`

**Use for:** Reports, articles, content drafts, analysis documents, calendars.

---

## 4. `create_spreadsheet`

Create a CSV spreadsheet with structured data.

**Args:**
```json
{
  "title": "Keyword Data Q1 2026",
  "data": "Keyword,Volume,Difficulty,CPC\nAI tools,45000,High,$3.50\nSEO trends,28000,Medium,$2.10"
}
```

**Use for:** Data tables, analytics exports, keyword lists, financial data.

---

## 5. `generate_image`

Generate an image using DALL-E (OpenAI).

**Args:**
```json
{
  "prompt": "Professional flat-lay photo of a luxury perfume bottle on marble background, soft lighting",
  "size": "1024x1024",
  "quality": "hd"
}
```

**Sizes:** `1024x1024` (default), `1792x1024` (landscape), `1024x1792` (portrait)
**Quality:** `standard` (default), `hd`

**Use for:** Social media visuals, marketing graphics, product mockups, illustrations.

**Requirements:** `OPENAI_API_KEY` configured in Settings.

---

## 6. `send_message`

Send a message to the human or other agents in the team chat.

**Args:**
```json
{ "message": "Weekly analytics report is ready. Engagement is up 12% this week." }
```

**Use for:** Status updates, asking for feedback, reporting results, team communication.

---

## 7. `file_operation`

Read, write, list, move, copy, or delete files on the system.

**Args:**
```json
{
  "operation": "write",
  "path": "/tmp/analysis-script.py",
  "content": "import json\n\ndata = {...}\nprint(json.dumps(data, indent=2))"
}
```

**Operations:**
| Operation | Required args | Description |
|-----------|--------------|-------------|
| `read` | `path` | Read file contents |
| `write` | `path`, `content` | Create or overwrite a file |
| `list` | `path` | List directory contents |
| `move` | `path`, `destination` | Move/rename a file |
| `copy` | `path`, `destination` | Copy a file |
| `delete` | `path` | Delete a file |

**Security:** Only allows operations within `$HOME` and `/tmp`.

**Use for:** Writing scripts, saving data, organizing files, creating code.

---

## 8. `run_command`

Execute a terminal/bash command.

**Args:**
```json
{ "command": "python3 /tmp/analysis-script.py" }
```

**Use for:** Running scripts, installing packages (`npm install`, `pip install`), system commands, data processing.

**Blocked commands:** `rm -rf /`, `mkfs`, `shutdown`, `reboot`, `passwd`, `sudo rm` (safety).

**Timeout:** 30 seconds per command.

---

## 9. `send_email`

Send an email via configured SMTP.

**Args:**
```json
{
  "to": "team@company.com",
  "subject": "Weekly Report - March 26",
  "body": "Hi team,\n\nHere's the weekly performance summary..."
}
```

**Requirements:** SMTP credentials configured in Settings.

---

## 10. `delegate`

Assign a task to another agent on the team. The target agent will pick it up on their next planning cycle as a priority task.

**Args:**
```json
{
  "to": "Social Media Manager",
  "task": "Create 3 Instagram posts based on these trending keywords: AI tools, sustainable tech, remote work tips. Use the keyword data from my latest SEO report."
}
```

**How it works:**
1. Agent A calls `delegate` with target agent name and task
2. Task is saved to the delegation queue (SQLite)
3. When Agent B replans, it sees the delegation as "PENDING TASKS"
4. Agent B executes the task and reports back

**Use for:** Cross-functional collaboration, splitting complex work, leveraging specialized agents.

---

## 11. `create_skill`

Create a reusable skill that all agents on the team can use. Skills are saved permanently and appear in the Skills panel.

**Args:**
```json
{
  "name": "Instagram Post Workflow",
  "description": "Complete workflow for creating and scheduling an Instagram post",
  "instructions": "1. Research trending hashtags with web_search\n2. Generate image with generate_image\n3. Write caption with engaging copy\n4. Schedule via Metricool using computer_use\n5. Report post URL and engagement predictions"
}
```

**Use for:** Saving processes that work, teaching other agents, building organizational knowledge.

---

## 12. `spawn_nano`

Launch a nano jelly — a mini-worker that executes a focused subtask in parallel with the parent agent.

**Args:**
```json
{
  "name": "Competitor Research Nano",
  "task": "Search for the top 5 competitors of 'Jellyfish AI' and create a comparison document with their features, pricing, and market position"
}
```

**Nano capabilities:** `web_search`, `create_document`, `generate_image`, `run_command`, `file_operation`, `create_skill`

**Max actions per nano:** 3

**Use for:** Parallelizing research, offloading subtasks, doing multiple things at once.

---

## Tool Combinations

The most effective agents combine tools strategically:

| Workflow | Tools used |
|----------|-----------|
| Research → Report | `web_search` → `create_document` |
| Keyword analysis → Content | `web_search` → `create_spreadsheet` → `delegate` to content agent |
| Write code → Execute | `file_operation` (write) → `run_command` |
| Visual content | `web_search` (inspiration) → `generate_image` → `create_document` (post copy) |
| Full automation | `web_search` → `file_operation` → `run_command` → `create_skill` (save the process) |
