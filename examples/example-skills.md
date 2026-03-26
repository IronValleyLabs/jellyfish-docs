# Example Skills

Skills are reusable procedures that agents create and share. Below are real-world examples of effective skills for different use cases.

---

## SEO & Content Skills

### Weekly Keyword Research

```json
{
  "name": "Weekly Keyword Research",
  "description": "Research and compile a weekly keyword report with search volumes, difficulty, and content recommendations",
  "instructions": "1. Use web_search to identify 5 trending topics in [industry]\n2. For each topic, search for 3-5 related long-tail keywords\n3. Use web_search to check current SERP for each keyword — note top 3 results\n4. Create a spreadsheet with columns: Keyword, Estimated Volume (High/Med/Low), Difficulty (High/Med/Low), Top Competitor, Content Gap\n5. Create a document with:\n   - Executive summary (3 bullet points)\n   - Data table of top 20 keywords\n   - Top 5 content opportunities with suggested titles\n   - Recommended action items\n6. Delegate top 5 keyword opportunities to Content Manager with suggested blog topics\n7. Send summary message to human with key findings"
}
```

### Blog Post Creation Workflow

```json
{
  "name": "Blog Post Creation Workflow",
  "description": "End-to-end process for researching, writing, and publishing an SEO-optimized blog post",
  "instructions": "1. Receive topic and target keyword from delegation or human request\n2. Use web_search to research the topic — find 5+ authoritative sources\n3. Use web_search to analyze top 5 ranking articles for the keyword\n4. Create outline with: Title (include keyword), H2/H3 headers (every 300 words), key points per section\n5. Write the full article (1500+ words) using create_document:\n   - Hook opening paragraph\n   - Data-backed claims with sources\n   - Practical examples and actionable tips\n   - H2/H3 structure for readability\n   - Conclusion with clear CTA\n6. Use generate_image to create a blog header image matching the topic\n7. Send completed draft to human for review via send_message"
}
```

---

## Social Media Skills

### Instagram Post Workflow

```json
{
  "name": "Instagram Post Workflow",
  "description": "Create a complete Instagram post with image, caption, and hashtags",
  "instructions": "1. Determine the post type: Educational, Engagement, Promotional, or Behind-the-scenes\n2. Use web_search to find trending hashtags related to [topic] — select 15-20 relevant ones\n3. Use generate_image to create a visually appealing image:\n   - Specify: modern, clean design\n   - Include brand colors if known\n   - HD quality\n4. Write caption following this structure:\n   - Hook line (question or bold statement)\n   - 2-3 value paragraphs\n   - Call-to-action (comment, save, share, or link in bio)\n   - Hashtag block (20 hashtags: 5 broad, 10 medium, 5 niche)\n5. Create document with image path, caption text, and posting notes\n6. Send message to human with the post for approval"
}
```

### Social Media Content Calendar

```json
{
  "name": "Weekly Content Calendar",
  "description": "Create a 7-day social media content calendar with post types, topics, and schedules",
  "instructions": "1. Use web_search to identify 3 trending topics in [industry] this week\n2. Use web_search to check for upcoming holidays, events, or awareness days\n3. Create a spreadsheet with columns: Day, Platform, Post Type, Topic, Caption Summary, Hashtags, Image Notes, Best Time to Post\n4. Fill in 7 days with this mix:\n   - Monday: Educational (tip or how-to)\n   - Tuesday: Engagement (poll or question)\n   - Wednesday: Product/promotional\n   - Thursday: Educational (industry insight)\n   - Friday: Behind-the-scenes or team culture\n   - Saturday: User-generated content or testimonial\n   - Sunday: Inspirational or week-ahead preview\n5. Create document with the calendar overview and any creative briefs needed\n6. Delegate image creation to Graphic Designer for posts needing custom visuals\n7. Send calendar to human for approval via send_message"
}
```

---

## Operations Skills

### Daily Server Health Check

```json
{
  "name": "Daily Server Health Check",
  "description": "Check server health metrics and create a status report",
  "instructions": "1. Use run_command to check system metrics:\n   - `uptime` — system load\n   - `df -h` — disk space\n   - `free -m` — memory usage\n   - `docker ps` — running containers (if applicable)\n2. Use run_command to check for errors:\n   - `tail -100 /var/log/syslog | grep -i error` (or relevant log path)\n3. Assess health status:\n   - GREEN: All metrics normal (disk < 80%, memory < 85%, load < 4.0)\n   - YELLOW: Warning (disk 80-90%, memory 85-95%, load 4-8)\n   - RED: Critical (disk > 90%, memory > 95%, load > 8, services down)\n4. Create document with:\n   - Status: GREEN/YELLOW/RED\n   - Metrics summary table\n   - Any errors found\n   - Recommended actions if YELLOW or RED\n5. If RED: Send immediate alert to human via send_message\n6. If GREEN/YELLOW: Include in daily summary message"
}
```

### Incident Postmortem

```json
{
  "name": "Incident Postmortem",
  "description": "Create a structured incident postmortem document after resolving a production issue",
  "instructions": "1. Gather incident details from recent messages, logs, and actions taken\n2. Create a document with the following structure:\n   ## Incident Postmortem: [Title]\n   ### Summary\n   - What happened (1-2 sentences)\n   - Impact (users affected, duration, severity)\n   - Resolution (how it was fixed)\n   ### Timeline\n   - [Time] — Issue first detected\n   - [Time] — Investigation started\n   - [Time] — Root cause identified\n   - [Time] — Fix implemented\n   - [Time] — Issue resolved and verified\n   ### Root Cause\n   - Technical explanation of what went wrong\n   ### What Went Well\n   - Detection time, response time, communication\n   ### What Could Be Improved\n   - Process gaps, monitoring gaps, documentation gaps\n   ### Action Items\n   - [ ] Specific preventive measures with owners\n   - [ ] Monitoring improvements\n   - [ ] Documentation updates\n3. Send postmortem document to human for review via send_message\n4. Delegate monitoring improvements to DevOps if applicable"
}
```

---

## Research & Analysis Skills

### Competitor Analysis

```json
{
  "name": "Competitor Analysis",
  "description": "Research a competitor and create a comprehensive profile document",
  "instructions": "1. Use web_search for '[competitor name] company overview' — get basic info\n2. Use web_search for '[competitor name] products pricing' — get offerings\n3. Use web_search for '[competitor name] reviews customers' — get sentiment\n4. Use web_search for '[competitor name] social media presence' — check channels\n5. Use web_search for '[competitor name] recent news announcements' — get latest updates\n6. Create a document with:\n   ## Competitor Profile: [Name]\n   ### Overview\n   - Founded, size, funding, market position\n   ### Products & Pricing\n   - Product list with pricing tiers\n   - Unique features vs our offering\n   ### Market Positioning\n   - Target audience\n   - Key messaging and value proposition\n   - Marketing channels used\n   ### Online Presence\n   - Website traffic estimate\n   - Social media followers and engagement\n   - Content strategy\n   ### SWOT Analysis\n   - Strengths, Weaknesses, Opportunities, Threats\n   ### Recommendations\n   - How we can differentiate\n   - Opportunities to exploit their weaknesses\n7. Send summary to human via send_message"
}
```

### Market Trend Report

```json
{
  "name": "Market Trend Report",
  "description": "Research and compile a market trend report for a specific industry",
  "instructions": "1. Use web_search for '[industry] trends 2024 2025' — identify top trends\n2. Use web_search for '[industry] market size growth forecast' — get market data\n3. Use web_search for '[industry] emerging technologies disruption' — find innovations\n4. Use web_search for '[industry] consumer behavior changes' — understand demand shifts\n5. Use spawn_nano to research 3 specific sub-trends in parallel for deeper analysis\n6. Create a document with:\n   ## Market Trend Report: [Industry]\n   ### Executive Summary (3 bullet points)\n   ### Market Overview\n   - Market size and growth rate\n   - Key players and market share estimates\n   ### Top 5 Trends\n   For each: Description, Impact, Timeline, Our Opportunity\n   ### Emerging Technologies\n   - Technologies disrupting the space\n   - Adoption timeline estimates\n   ### Consumer Insights\n   - Behavior changes and preferences\n   - Demand patterns\n   ### Strategic Recommendations\n   - Ranked by impact and feasibility\n   - Specific next steps for each\n7. Create a spreadsheet with trend data for further analysis\n8. Delegate content opportunities to Content Manager\n9. Send executive summary to human via send_message"
}
```
