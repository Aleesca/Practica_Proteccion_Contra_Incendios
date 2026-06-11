---
name: nlm-skill
description: "Expert guide for the NotebookLM CLI (`nlm`) interface for Google NotebookLM. Use this skill when users want to interact with NotebookLM programmatically via terminal commands, including: creating/managing notebooks, adding sources (URLs, YouTube, text, Google Drive), generating content (podcasts, reports, quizzes, flashcards, mind maps, slides, infographics, videos, data tables), conducting research, chatting with sources, or automating NotebookLM workflows. Triggers on mentions of \"nlm\", \"notebooklm\", \"notebook lm\", \"podcast generation\", \"audio overview\", or any NotebookLM-related automation task."
version: "0.6.1"
---

# NotebookLM CLI Expert

This skill provides comprehensive guidance for using NotebookLM through the `nlm` CLI.

## Quick Reference

Run `nlm --ai` to get comprehensive AI-optimized documentation for the installed CLI.

```bash
nlm --help              # List all commands
nlm <command> --help    # Help for a specific command
nlm --ai                # Full AI-optimized documentation
nlm --version           # Check installed version
```

## Critical Rules

1. **Always authenticate first**: Run `nlm login` before any NotebookLM operation.
2. **Sessions expire in ~20 minutes**: Re-run `nlm login` if commands start failing with authentication errors.
3. **Always ask before delete**: Before executing any delete command, ask the user for explicit confirmation. Deletions are irreversible. Show what will be deleted and warn about permanent data loss.
4. **`--confirm` is required**: All generation and delete commands need `--confirm` or `-y`.
5. **Research requires `--notebook-id`**: The flag is mandatory, not positional.
6. **Capture IDs from output**: Create/start commands return IDs needed for subsequent operations.
7. **Use aliases**: Simplify long UUIDs with `nlm alias set <name> <uuid>`.
8. **Check aliases before creating**: Run `nlm alias list` before creating a new alias to avoid conflicts.
9. **Do not launch the REPL for automation**: Never use `nlm chat start` in AI-controlled workflows. Use `nlm notebook query` for one-shot Q&A.
10. **Choose output format wisely**: Default output is compact and token-efficient for status checks. Use `--quiet` to capture IDs for piping. Use `--json` when parsing fields programmatically.
11. **Use `--help` when unsure**: Run `nlm <command> --help` to confirm available options and flags.

## Workflow Decision Tree

Use this to determine the right sequence of commands:

```text
User wants to...
|
+-- Work with NotebookLM for the first time
|   `-- nlm login -> nlm notebook create "Title"
|
+-- Add content to a notebook
|   +-- From a URL/webpage -> nlm source add <nb-id> --url "https://..."
|   +-- From YouTube -> nlm source add <nb-id> --url "https://youtube.com/..."
|   +-- From pasted text -> nlm source add <nb-id> --text "content" --title "Title"
|   +-- From Google Drive -> nlm source add <nb-id> --drive <doc-id> --type doc
|   `-- Discover new sources -> nlm research start "query" --notebook-id <nb-id>
|
+-- Generate content from sources
|   +-- Podcast/Audio -> nlm audio create <nb-id> --confirm
|   +-- Written summary -> nlm report create <nb-id> --confirm
|   +-- Study materials -> nlm quiz/flashcards create <nb-id> --confirm
|   +-- Visual content -> nlm mindmap/slides/infographic create <nb-id> --confirm
|   +-- Video -> nlm video create <nb-id> --confirm
|   `-- Extract data -> nlm data-table create <nb-id> "description" --confirm
|
+-- Ask questions about sources
|   `-- nlm notebook query <nb-id> "question"
|       Use --conversation-id for follow-ups.
|       Do not use `nlm chat start`; it is an interactive REPL.
|
+-- Check generation status
|   `-- nlm studio status <nb-id>
|
`-- Manage/cleanup
    +-- List notebooks -> nlm notebook list
    +-- List sources -> nlm source list <nb-id>
    +-- Delete source -> nlm source delete <source-id> --confirm
    `-- Delete notebook -> nlm notebook delete <nb-id> --confirm
```

## Command Categories

### 1. Authentication

```bash
nlm login                            # Launch browser and authenticate
nlm login --check                    # Validate current session
nlm login --profile work             # Use named profile for multiple accounts
nlm login --provider openclaw --cdp-url http://127.0.0.1:18800
nlm login switch <profile>           # Switch the default profile
nlm login profile list               # List profiles with email addresses
nlm login profile delete <name>      # Delete a profile
nlm login profile rename <old> <new> # Rename a profile
```

Multi-profile support gives each profile its own isolated browser session for multiple Google accounts.

### 2. Notebook Management

```bash
nlm notebook list                      # List all notebooks
nlm notebook list --json               # JSON output for parsing
nlm notebook list --quiet              # IDs only for scripting
nlm notebook create "Title"            # Create notebook, returns ID
nlm notebook get <id>                  # Get notebook details
nlm notebook describe <id>             # AI-generated summary + suggested topics
nlm notebook query <id> "question"     # One-shot Q&A with sources
nlm notebook rename <id> "New Title"   # Rename notebook
nlm notebook delete <id> --confirm     # Permanent deletion
```

### 3. Source Management

```bash
# Adding sources
nlm source add <nb-id> --url "https://..."              # Web page
nlm source add <nb-id> --url "https://youtube.com/..."  # YouTube video
nlm source add <nb-id> --text "content" --title "X"     # Pasted text
nlm source add <nb-id> --drive <doc-id>                 # Drive doc, auto-detect type
nlm source add <nb-id> --drive <doc-id> --type slides   # Explicit Drive type

# Listing and viewing
nlm source list <nb-id>                    # Table of sources
nlm source list <nb-id> --drive            # Show Drive sources with freshness
nlm source list <nb-id> --drive -S         # Skip freshness checks
nlm source get <source-id>                 # Source metadata
nlm source describe <source-id>            # AI summary + keywords
nlm source content <source-id>             # Raw text content
nlm source content <source-id> -o file.txt # Export raw text

# Drive sync
nlm source stale <nb-id>                                  # List outdated Drive sources
nlm source sync <nb-id> --confirm                         # Sync all stale sources
nlm source sync <nb-id> --source-ids <ids> --confirm       # Sync specific sources

# Rename
nlm source rename <source-id> "New Title" --notebook <nb-id>
nlm rename source <source-id> "New Title" --notebook <nb-id>

# Deletion
nlm source delete <source-id> --confirm
```

Drive types: `doc`, `slides`, `sheets`, `pdf`.

### 4. Research

Research finds new sources from the web or Google Drive.

```bash
# Start research; --notebook-id is required
nlm research start "query" --notebook-id <id>                 # Fast web research
nlm research start "query" --notebook-id <id> --mode deep     # Deep web research
nlm research start "query" --notebook-id <id> --source drive  # Drive search

# Check progress
nlm research status <nb-id>                  # Poll until done
nlm research status <nb-id> --max-wait 0     # Single check
nlm research status <nb-id> --task-id <tid>  # Check specific task
nlm research status <nb-id> --full           # Full details

# Import discovered sources
nlm research import <nb-id> <task-id>                    # Import all
nlm research import <nb-id> <task-id> --indices 0,2,5    # Import specific
nlm research import <nb-id> <task-id> --timeout 600      # Custom timeout
```

Modes: `fast` is quicker and returns fewer sources; `deep` takes longer and is web-only.

### 5. Content Generation

All generation commands require `--confirm` or `-y`. Common flags include:

- `--source-ids <id1,id2>`: limit generation to specific sources.
- `--language <code>`: BCP-47 code such as `en`, `es`, `fr`, `de`, `ja`.

```bash
# Audio
nlm audio create <id> --confirm
nlm audio create <id> --format deep_dive --length default --confirm
nlm audio create <id> --format brief --focus "key topic" --confirm
# Formats: deep_dive, brief, critique, debate
# Lengths: short, default, long

# Report
nlm report create <id> --confirm
nlm report create <id> --format "Study Guide" --confirm
nlm report create <id> --format "Create Your Own" --prompt "Custom..." --confirm
# Formats: "Briefing Doc", "Study Guide", "Blog Post", "Create Your Own"

# Quiz
nlm quiz create <id> --confirm
nlm quiz create <id> --count 5 --difficulty 3 --confirm
nlm quiz create <id> --count 10 --difficulty 3 --focus "Exam prep" --confirm

# Flashcards
nlm flashcards create <id> --confirm
nlm flashcards create <id> --difficulty hard --confirm
nlm flashcards create <id> --difficulty medium --focus "Focus on definitions" --confirm

# Mind map
nlm mindmap create <id> --confirm
nlm mindmap create <id> --title "Topic Overview" --confirm
nlm mindmap list <id>

# Slides
nlm slides create <id> --confirm
nlm slides create <id> --format presenter --length short --confirm
nlm slides revise <artifact-id> --slide '1 Make the title larger' --confirm

# Infographic
nlm infographic create <id> --confirm
nlm infographic create <id> --orientation portrait --detail detailed --style professional --confirm

# Video
nlm video create <id> --confirm
nlm video create <id> --format brief --style whiteboard --confirm

# Data table
nlm data-table create <id> "Extract all dates and events" --confirm
```

### 6. Studio Artifact Management

```bash
# Check status
nlm studio status <nb-id>          # List all artifacts
nlm studio status <nb-id> --full   # Show full details
nlm studio status <nb-id> --json   # JSON output

# Download artifacts
nlm download audio <nb-id> --output podcast.mp3
nlm download video <nb-id> --output video.mp4
nlm download report <nb-id> --output report.md
nlm download slide-deck <nb-id> --output slides.pdf
nlm download slide-deck <nb-id> --output slides.pptx --format pptx
nlm download quiz <nb-id> --output quiz.json --format json

# Export to Google Docs/Sheets
nlm export sheets <nb-id> <artifact-id> --title "My Data Table"
nlm export docs <nb-id> <artifact-id> --title "My Report"

# Rename and delete artifacts
nlm studio rename <artifact-id> "New Title"
nlm rename studio <artifact-id> "New Title"
nlm studio delete <nb-id> <artifact-id> --confirm
```

Status values include `completed`, `in_progress`, and `failed`.

### 7. Chat Configuration and Notes

Use `nlm notebook query` for automated one-shot questions.

```bash
nlm notebook query <nb-id> "What are the key findings?"
nlm notebook query <nb-id> "Follow-up question" --conversation-id <conversation-id>
```

For human terminal use only:

```bash
nlm chat start <nb-id>
```

The chat REPL is interactive and should not be used in AI-controlled workflows.

```bash
# Configure chat behavior
nlm chat configure <id> --goal default
nlm chat configure <id> --goal learning_guide
nlm chat configure <id> --goal custom --prompt "Act as a tutor..."
nlm chat configure <id> --response-length longer

# Notes
nlm note create <nb-id> "Content" --title "Title"
nlm note list <nb-id>
nlm note update <nb-id> <note-id> --content "New content"
nlm note delete <nb-id> <note-id> --confirm
```

### 8. Notebook Sharing

```bash
nlm share status <nb-id>
nlm share public <nb-id>           # Enable public link
nlm share public <nb-id> --off     # Disable public link
nlm share invite <nb-id> user@example.com
nlm share invite <nb-id> user@example.com --role editor
```

### 9. Aliases

Use aliases to avoid repeating long IDs.

```bash
nlm alias set myproject abc123-def456...
nlm alias get myproject
nlm alias list
nlm alias delete myproject

nlm notebook get myproject
nlm source list myproject
nlm audio create myproject --confirm
```

### 10. Configuration

```bash
nlm config show
nlm config get <key>
nlm config set <key> <value>
nlm config set output.format json
nlm login switch work
```

Available settings:

| Key | Default | Description |
|-----|---------|-------------|
| `output.format` | `table` | Default output format: `table` or `json` |
| `output.color` | `true` | Enable colored output |
| `output.short_ids` | `true` | Show shortened IDs |
| `auth.browser` | `auto` | Preferred browser for login |
| `auth.default_profile` | `default` | Profile to use when `--profile` is not specified |

### 11. Skill Management

Manage the NotebookLM skill installation for AI assistants:

```bash
nlm skill list
nlm skill update
nlm skill update <tool>
nlm skill install <tool>
nlm skill uninstall <tool>
```

Verb-first aliases include `nlm update skill`, `nlm list skills`, and `nlm install skill`.

### 12. Output Formats

Most list commands support multiple formats:

| Flag | Description |
|------|-------------|
| none | Rich table, human-readable |
| `--json` | JSON output for parsing |
| `--quiet` | IDs only for piping |
| `--title` | `ID: Title` format |
| `--url` | `ID: URL` format for sources |
| `--full` | All columns or details |

### 13. Batch Operations

Perform the same action across multiple notebooks.

```bash
nlm batch query "What are the key takeaways?" --notebooks "id1,id2"
nlm batch query "Summarize" --tags "ai,research"
nlm batch query "Summarize" --all
nlm batch add-source --url "https://..." --notebooks "id1,id2"
nlm batch create "Project A, Project B, Project C"
nlm batch delete --notebooks "id1,id2" --confirm
nlm batch studio --type audio --tags "research" --confirm
```

### 14. Cross-Notebook Query

Query multiple notebooks and get aggregated answers with per-notebook citations.

```bash
nlm cross query "What features are discussed?" --notebooks "id1,id2"
nlm cross query "Compare approaches" --tags "ai,research"
nlm cross query "Summarize everything" --all
```

### 15. Pipelines

Define and execute multi-step notebook workflows.

```bash
nlm pipeline list
nlm pipeline run <notebook> ingest-and-podcast --url "https://..."
nlm pipeline run <notebook> research-and-report --url "https://..."
nlm pipeline run <notebook> multi-format
nlm pipeline create <name> --file <pipeline.yaml>
```

Built-in pipelines:

- `ingest-and-podcast`: add source, then generate audio.
- `research-and-report`: research, import, then generate report.
- `multi-format`: generate audio, report, and flashcards.

### 16. Tags and Smart Select

Tag notebooks for organization and use tags to target batch operations.

```bash
nlm tag add <notebook> --tags "ai,research,llm"
nlm tag add <notebook> --tags "ai" --title "My Notebook"
nlm tag remove <notebook> --tags "ai"
nlm tag list
nlm tag select "ai research"
```

### 17. Diagnostics

Use diagnostics for installation, authentication, browser, and profile issues.

```bash
nlm doctor
nlm doctor --verbose
```

## Common Patterns

### Pattern 1: Research to Podcast

```bash
nlm notebook create "AI Research 2026"
nlm alias set ai <notebook-id>
nlm research start "agentic AI trends" --notebook-id ai --mode deep
nlm research status ai --max-wait 300
nlm research import ai <task-id>
nlm audio create ai --format deep_dive --confirm
nlm studio status ai
```

### Pattern 2: Quick Content Ingestion

```bash
nlm source add <id> --url "https://example1.com"
nlm source add <id> --url "https://example2.com"
nlm source add <id> --text "My notes..." --title "Notes"
nlm source list <id>
```

### Pattern 3: Study Materials

```bash
nlm report create <id> --format "Study Guide" --confirm
nlm quiz create <id> --count 10 --difficulty 3 --focus "Exam prep" --confirm
nlm flashcards create <id> --difficulty medium --focus "Core terms" --confirm
```

### Pattern 4: Drive Document Workflow

```bash
nlm source add <id> --drive 1KQH3eW0hMBp7WK... --type slides
nlm source stale <id>
nlm source sync <id> --confirm
```

### Pattern 5: Batch and Cross-Notebook Workflow

```bash
nlm tag add <id1> --tags "ai,research"
nlm tag add <id2> --tags "ai,product"
nlm cross query "What are the main conclusions?" --tags "ai"
nlm batch studio --type audio --tags "ai" --confirm
nlm pipeline run <id> ingest-and-podcast --url "https://example.com"
```

## Error Recovery

| Error | Cause | Solution |
|-------|-------|----------|
| `Cookies have expired` | Session timeout | `nlm login` |
| `authentication may have expired` | Session timeout | `nlm login` |
| `Notebook not found` | Invalid ID | `nlm notebook list` |
| `Source not found` | Invalid ID | `nlm source list <nb-id>` |
| `Rate limit exceeded` | Too many calls | Wait 30 seconds, retry |
| `Research already in progress` | Pending research | Use `--force` or import first |
| `Import timed out` | Too many sources | Use `--timeout 600` |
| `Google API error code 3` | Transient deep research error | Retry later or use `--mode fast` |
| `Browser doesn't launch` | Port conflict | Close browser, retry |

## Rate Limiting

Wait between operations to avoid rate limits:

- Source operations: 2 seconds.
- Content generation: 5 seconds.
- Research operations: 2 seconds.
- Query operations: 2 seconds.

## Advanced Reference

For detailed information, see:

- [references/command_reference.md](references/command_reference.md): Complete command signatures.
- [references/troubleshooting.md](references/troubleshooting.md): Detailed error handling.
- [references/workflows.md](references/workflows.md): End-to-end task sequences.
