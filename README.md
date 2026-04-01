# Apartment Hunt — Claude-Powered Search Agent

A personal apartment search system powered by Claude Code. Fork it, configure your criteria, and Claude will search listings, track candidates, and run a daily automated sweep to catch price changes and new availability.

## How It Works

- **`/search-apartments [neighborhood]`** — Search for new listings matching your criteria and summarize candidates
- **`/explore-my-options`** — Fetch live StreetEasy listings for all active candidates and check each unit against requirements
- **Daily cron agent** — Runs automatically each morning, checks existing candidates for status changes, and searches for new leads
- **Structured markdown files** — All candidates tracked in plain Markdown; easy to read, edit, and version-control

## Forking for Your Own Search

1. **Fork this repo**
2. **Edit `CLAUDE.md`** — Replace the search criteria with your own (city, budget, must-haves)
3. **Replace the search files** — Create your own `[borough]_apartment_search.md` files based on the existing examples
4. **Open Claude Code** in your fork — The skills will automatically pick up your criteria from `CLAUDE.md`
5. **Set up the daily cron** (optional) — See [Scheduling](#scheduling) below

## File Structure

```
├── CLAUDE.md                        ← Search criteria (edit this to configure)
├── brooklyn_apartment_search.md     ← Brooklyn candidates
├── manhattan_apartment_search.md    ← Manhattan candidates
├── options/                         ← Saved results from /explore-my-options
│   └── YYYY-MM-DD-neighborhoods.md  ← Dated snapshots of live availability
└── .claude/
    └── skills/
        ├── search-apartments/
        │   └── SKILL.md             ← Find new candidates
        └── explore-my-options/
            └── SKILL.md             ← Check live listings against criteria
```

## Using the Skills

### /search-apartments

Search for new candidates in a specific area:

```
/search-apartments
/search-apartments Brooklyn waterfront
/search-apartments Hell's Kitchen
/search-apartments 8 Spruce Street
```

Claude will read your current candidates, search for new listings, check parking (including motorcycle if relevant), and ask if you want to add anything to the tracking files.

### /explore-my-options

Check what's actually available right now across all your active candidates:

```
/explore-my-options
```

Claude will fetch live StreetEasy listings for every active building, cross-check each unit against your hard requirements, and save a dated report to `options/`.

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
- Claude Max, Pro, or Team plan for the skills
- Claude Max or Team plan for the daily cron agent
