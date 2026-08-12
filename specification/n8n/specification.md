# Specification: n8n

> **Guidelines**: Read [guidelines.md](../guidelines.md) and [guidelines-n8n-workflow.md](../guidelines-n8n-workflow.md) before executing ANY tasks below. Follow all constraints described there throughout execution.

## Basic Setup

- [x] Read the project input (`product-requirements-document.md`, `intent.md`)

## Workflow: Daily Multilingual Morning Greeting

- [x] Create a single n8n workflow file `assets/n8n/workflows/daily-multilingual-greeting.n8n.json`
- [x] Add a **Schedule Trigger** node that fires every day at 08:00 AM (cron: `0 8 * * *`)
- [x] Add a **Code (Function) node** named `Select Language` that:
  - Maintains an ordered list of at least 10 greetings in different languages, e.g.:
    - English: "Good morning! ☀️"
    - Spanish: "¡Buenos días! ☀️"
    - French: "Bonjour! ☀️"
    - German: "Guten Morgen! ☀️"
    - Japanese: "おはようございます！☀️"
    - Portuguese: "Bom dia! ☀️"
    - Arabic: "صباح الخير! ☀️"
    - Mandarin: "早上好！☀️"
    - Hindi: "सुप्रभात! ☀️"
    - Swahili: "Habari za asubuhi! ☀️"
  - Determines the current day index using `new Date().getDay()` (or day-of-year) to rotate through languages
  - Returns the selected `language` name and `greeting` text
- [x] Add a **Set node** named `Compose Message` that builds the full message string, e.g.:
  `"🌍 Today's greeting is in {{language}}: {{greeting}}"`
- [x] Add a **delivery node** (default: Slack → `Send a message`) named `Send Greeting` that:
  - Sends the composed message to a configurable channel (use placeholder `#general` as default)
  - Does NOT include a credentials block (user configures credentials manually in n8n UI after import)
- [x] Connect nodes in order: `Schedule Trigger` → `Select Language` → `Compose Message` → `Send Greeting`
- [x] Ensure `connections` reference nodes by `name`, not `id`
- [x] Validate all workflow JSON files are well-formed
