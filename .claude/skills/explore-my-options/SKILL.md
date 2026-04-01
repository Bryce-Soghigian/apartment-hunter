---
name: explore-my-options
description: Show a quick-reference summary of all active apartment candidates with links, prices, and one-line descriptions. Use when the user wants an overview of current options or wants to browse what's been found so far.
user-invocable: true
allowed-tools: Read, WebSearch
---

Read both search files and produce a clean, scannable overview of every active (non-ruled-out) candidate.

Files to read:
- `brooklyn_apartment_search.md`
- `manhattan_apartment_search.md`

After reading the files, for each active candidate that does not already have a direct StreetEasy listing URL (i.e. a URL pointing to a specific unit or active listing, not just the building page), do a quick WebSearch for: `site:streeteasy.com "[Building Name]" "[Address]" rentals` to find a direct link to current listings. Prefer a URL that goes directly to available units (e.g. streeteasy.com/buildings/... or streeteasy.com/for-rent/...) over the generic building website.

## Output Format

Group by borough. For each active candidate output one block:

**Building Name** — Neighborhood
> One-sentence description of what makes it stand out.
- Price: $X,XXX/mo (+ notes on concessions if any)
- Parking: [confirmed/TBD/off-site]
- Den/Office: [confirmed/unconfirmed]
- Listings: [direct StreetEasy link to available units, or building website if no StreetEasy found]

Skip anything in "Ruled Out" sections. At the end, add a one-line count: "X candidates total (Y Brooklyn, Z Manhattan)."
