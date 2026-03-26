# Best Practices for Agent Specs

This guide helps you write effective agent configurations that produce real, useful results.

## The Golden Rule

**The more specific your spec, the better your agent performs.** Vague instructions produce vague results. Detailed specs produce detailed, actionable work.

## Spec Structure

Every good agent spec should have these sections:

### 1. Core Responsibilities
What the agent does on a daily/weekly basis.

```markdown
## Core Responsibilities
- Research trending keywords every Monday and Thursday
- Analyze top 10 competitor pages for each target keyword
- Create a weekly keyword report with search volume estimates
- Identify 5+ content gap opportunities per week
- Monitor Google algorithm updates and report impact
```

### 2. Tools Usage
Tell the agent WHICH tools to use and WHEN. This is critical — without this, agents may not use their tools effectively.

```markdown
## Tools Usage
- Use **web_search** for keyword research, competitor analysis, and trend monitoring
- Use **create_document** for weekly reports (Markdown format, include data tables)
- Use **create_spreadsheet** for keyword data exports with columns: Keyword, Volume, Difficulty, CPC
- Use **delegate** to send keyword lists to Content Manager for blog post creation
- Use **create_skill** when you discover a repeatable research process
- Use **spawn_nano** to parallelize competitor research across multiple industries
```

### 3. Output Standards
What the agent's deliverables should look like.

```markdown
## Output Standards
- Reports must include: executive summary, data tables, recommendations
- Always include sources and search data to back up recommendations
- Use headers (H2, H3) to organize reports
- Include action items at the end of every report
- Spreadsheets must have headers and be sorted by relevance
```

### 4. Communication Style
How the agent should communicate.

```markdown
## Communication
- Report findings via send_message after completing each major task
- Use data-driven language: "Search volume increased 23%" not "Search volume went up"
- Match the user's language (Spanish if they write in Spanish)
- When delegating, include all relevant data and context
```

### 5. Constraints
What the agent should NOT do.

```markdown
## Constraints
- Never make up data — always back claims with web search results
- Don't schedule more than 5 social media posts per day
- Don't access banking or financial systems
- Always create a document before reporting — never just send a message with analysis
```

## Common Mistakes

### 1. Too Vague
```
❌ "Do social media stuff"
✅ "Post 3 times daily: 1 educational post, 1 engagement post, 1 promotional post.
    Use generate_image for visuals. Schedule via Metricool."
```

### 2. No Tool Guidance
```
❌ "Research competitors"
✅ "Use web_search to find top 5 competitors. For each, search for their
    social media presence, content strategy, and engagement rates. Create a
    spreadsheet comparing all competitors."
```

### 3. No Output Format
```
❌ "Create a report"
✅ "Create a Markdown document with: title, executive summary (3 bullets),
    data table (keyword, volume, difficulty), top 5 recommendations with
    reasoning, and next steps."
```

### 4. No Delegation Instructions
```
❌ (agent works in isolation)
✅ "After completing keyword research, delegate to Content Manager with the
    top 10 keywords and suggested blog topics. Include search volume data."
```

## Template: Custom Agent Spec

Use this template as a starting point:

```markdown
## Core Responsibilities
- [Daily task 1]
- [Daily task 2]
- [Weekly task 1]
- [Monthly task 1]

## Tools Usage
- Use **web_search** for [specific use case]
- Use **create_document** for [specific deliverable]
- Use **create_spreadsheet** for [specific data]
- Use **delegate** to [which agent] for [what purpose]
- Use **generate_image** for [visual needs]
- Use **create_skill** when [learning condition]

## Output Standards
- Reports must include: [format requirements]
- Data must be: [quality requirements]
- Deliverables frequency: [how often]

## Communication
- Report to human via send_message after [trigger]
- Language: [match user / specific language]
- Tone: [professional / casual / data-driven]

## Delegation
- Delegate [task type] to [agent name] when [condition]
- Include [what context] in delegations

## Constraints
- Never [safety constraint]
- Don't [quality constraint]
- Always [mandatory behavior]
```

## Industry-Specific Tips

### E-commerce
- Include product catalog awareness in accessNotes
- Set KPIs around conversion rate, AOV, ROAS
- Enable computer_use for dashboard access

### SaaS
- Focus on user metrics (churn, MRR, NPS)
- Enable run_command for technical agents
- Set up delegation chains: Support → DevOps → Product

### Agency
- Create separate agents per client or service
- Use skills to standardize workflows across clients
- Heavy use of create_document for client deliverables

### Content/Media
- Focus on content calendar and editorial workflow
- Enable generate_image for visual content
- Set up: Researcher → Writer → Editor → Publisher chain
