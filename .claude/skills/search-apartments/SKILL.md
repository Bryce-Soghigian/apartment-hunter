---
name: search-apartments
description: Search for NYC apartments matching the hunt criteria (1BR, <$4,700/mo, F2C windows, in-unit W/D, gym, highrise preferred). Use when the user wants to find new candidates or research a specific building/neighborhood.
disable-model-invocation: true
allowed-tools: Read, WebSearch, WebFetch, Edit, Write
---

Search for NYC apartments matching these criteria:
- **Unit**: 1BR or larger
- **Rent**: Under $4,700/month
- **Required amenities**: floor-to-ceiling windows, in-unit washer/dryer, gym
- **Preferred**: highrise, den/office, walk-in closet, balcony
- **Lifestyle amenities to note** (not dealbreakers, but major pluses):
  - Piano or music room
  - Co-working space / business center / library lounge
  - Standout gym features (pool, rock climbing, basketball, etc.)

## Arguments

$ARGUMENTS should specify a neighborhood, borough, or specific building name. If blank, search broadly across Brooklyn and Manhattan.

## Steps

1. Read the relevant search file(s) to understand current candidates and what's already been ruled out:
   - Brooklyn leads: `brooklyn_apartment_search.md`
   - Manhattan leads: `manhattan_apartment_search.md`

2. Search for new listings and buildings using WebSearch. Good search queries:
   - `"[neighborhood] NYC 1BR den apartment floor to ceiling windows in-unit laundry parking" site:streeteasy.com OR site:apartments.com`
   - `"[building name] NYC apartments parking motorcycle"`
   - `"[neighborhood] highrise rental apartments NYC 2026"`

3. For each promising candidate, verify parking availability (especially motorcycle — this is commonly overlooked; call or check building FAQ if needed).

4. **CRITICAL: Verify actual 1-bedroom pricing from ACTIVE listings only.** NYC rents have increased significantly — old/cached data is useless.
   - **Only use prices from currently active listings** — never from "no longer available", "in contract", historical data, or old articles
   - Search specifically for "1 bedroom" or "1BR" pricing, not just the building's lowest price
   - If a price seems suspiciously low (e.g., under $3,500 in Manhattan/prime Brooklyn), confirm it's actually for a 1BR
   - Use queries like `"[building name]" "1 bedroom" rent 2026 site:streeteasy.com` to find current unit-specific pricing
   - When in doubt, note the price as "unverified — may be studio or stale pricing" and flag for follow-up
   - If you can only find old pricing data, explicitly state "NO ACTIVE LISTINGS FOUND — pricing unverified"

5. Summarize findings: for each new candidate include:
   - Building name and address
   - **Verified 1BR rent** (not "starting at" price) — mark as "unverified" if you couldn't confirm
   - Which required amenities are confirmed vs unconfirmed
   - Parking situation (car + motorcycle — note if motorcycle parking is unclear)
   - Lifestyle amenities (write a brief paragraph noting): piano/music room, gym highlights (pool, climbing, basketball), co-working/business center
   - Any deal-breakers or notable pros/cons

6. Ask the user if they want to add any candidates to the relevant markdown file.
