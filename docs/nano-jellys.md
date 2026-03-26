# Nano Jellys

Nano jellys are lightweight mini-workers that agents can spawn to handle subtasks in parallel. They're fast, focused, and disposable.

## How They Work

```
Parent agent needs to do multiple things
    ↓
Spawns a nano jelly with a specific task
    ↓
Nano gets its own LLM call to plan (max 3 actions)
    ↓
Nano executes its actions independently
    ↓
Nano summarizes results with another LLM call
    ↓
Summary reported back to parent agent's chat
```

## Nano Capabilities

Nano jellys have access to 6 tools:

| Tool | Description |
|------|-------------|
| `web_search` | Search the web for information |
| `create_document` | Create markdown/HTML documents |
| `generate_image` | Generate images with DALL-E |
| `run_command` | Execute bash/terminal commands |
| `file_operation` | Read, write, list files |
| `create_skill` | Save a reusable skill |

**Limitations:**
- Max 3 actions per nano
- No `computer_use` (browser control)
- No `delegate` (can't delegate to other agents)
- No `send_email`

## When to Use Nano Jellys

**Good use cases:**
- Research while the parent agent does something else
- Generate an image while writing a report
- Run a script while searching for data
- Quick, focused subtasks that don't need full agent capabilities

**Spawning example:**
```json
{
  "name": "Competitor Research",
  "task": "Search for the top 3 competitors of Jellyfish AI and create a comparison document with features and pricing"
}
```

## Nano vs. Delegation

| Feature | Nano Jelly | Delegation |
|---------|-----------|------------|
| Speed | Immediate (same cycle) | Next planning cycle |
| Autonomy | Limited (3 actions) | Full agent capabilities |
| Tools | 6 tools | 12 tools |
| Persistence | Disposable | Tracked in queue |
| Use case | Quick subtasks | Complex, specialized work |

**Rule of thumb:** Use nano jellys for quick research/generation tasks. Use delegation for work that needs a specialist agent's full capabilities.
