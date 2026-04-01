---
name: explore-my-options
description: Show a quick-reference summary of all active apartment candidates with links, prices, and one-line descriptions. Use when the user wants an overview of current options or wants to browse what's been found so far.
user-invocable: true
allowed-tools: Read
---

Read both search files and produce a clean, scannable overview of every active (non-ruled-out) candidate.

Files to read:
- `brooklyn_apartment_search.md`
- `manhattan_apartment_search.md`

## Output Format

Group by borough. For each active candidate output one block:

**Building Name** — Neighborhood
> One-sentence description of what makes it stand out.
- Price: $X,XXX/mo (+ notes on concessions if any)
- Parking: [confirmed/TBD/off-site]
- Den/Office: [confirmed/unconfirmed]
- Website or StreetEasy link (if available in the file)

Skip anything in "Ruled Out" sections. At the end, add a one-line count: "X candidates total (Y Brooklyn, Z Manhattan)."
