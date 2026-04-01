# Apartment Hunt — Claude-Powered Search Agent

A personal apartment search system powered by Claude Code. Fork it, configure your criteria, and Claude will search listings, track candidates, and run a daily automated sweep to catch price changes and new availability.

## How It Works

- **`/search-apartments [neighborhood]`** — Slash command that searches for new listings matching your criteria and summarizes candidates
- **Daily cron agent** — Runs automatically each morning, checks existing candidates for status changes, and searches for new leads
- **Structured markdown files** — All candidates tracked in plain Markdown; easy to read, edit, and version-control

## Forking for Your Own Search

1. **Fork this repo**
2. **Edit `CLAUDE.md`** — Replace the search criteria with your own (city, budget, must-haves)
3. **Replace the search files** — Use `template/search.template.md` as a starting point; delete the existing borough files or replace with your own
4. **Open Claude Code** in your fork — The `/search-apartments` skill will automatically pick up your criteria from `CLAUDE.md`
5. **Set up the daily cron** (optional) — See [Scheduling](#scheduling) below

## File Structure

```
├── CLAUDE.md                        ← Search criteria (edit this to configure)
├── brooklyn_apartment_search.md     ← Brooklyn candidates (example)
├── manhattan_apartment_search.md    ← Manhattan candidates (example)
├── .claude/
│   └── skills/
│       └── search-apartments/
│           └── SKILL.md             ← The search slash command
└── template/
    ├── CLAUDE.template.md           ← Blank criteria template
    └── search.template.md           ← Blank candidate tracking template
```

## Using the Skill

In Claude Code, run:

```
/search-apartments
/search-apartments Brooklyn waterfront
/search-apartments Hell's Kitchen
/search-apartments 8 Spruce Street
```

Claude will read your current candidates, search for new listings, check parking (including motorcycle if relevant), and ask if you want to add anything to the tracking files.

## Scheduling

The daily cron agent runs as a remote Claude Code session (requires a [Claude Max or Team plan](https://claude.ai)). It:

1. Reads your current candidate files
2. Searches for new listings matching your criteria
3. Checks existing candidates for price changes, new concessions, or units going off-market
4. Commits any updates back to the repo with a dated status note

To set up the cron for your fork, open Claude Code and run:
```
/schedule
```
Then describe: "Daily at 9am, search for new apartments and reverify existing candidates in [your search files], commit any changes."

## Candidate File Format

Each search file follows this structure:

```markdown
## Active Candidates

### Building Name
**Address**
- Key amenity details
- Last verified: YYYY-MM-DD

| Detail | Info |
|---|---|
| Price | From $X,XXX/mo |
| Parking | Details |
| Den/Office | Confirmed / Unconfirmed |

## Ruled Out

| Building | Reason |
|---|---|
| Name | Why eliminated |

## Parking Notes
...
```

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
- Claude Max, Pro, or Team plan for the `/search-apartments` skill
- Claude Max or Team plan for the daily cron agent
