---
name: search-apartments
description: Search for NYC apartments matching the hunt criteria (1BR+den, <$4,700/mo, F2C windows, in-unit W/D, gym, car+motorcycle parking, highrise preferred). Use when the user wants to find new candidates or research a specific building/neighborhood.
disable-model-invocation: true
allowed-tools: Read, WebSearch, WebFetch, Edit, Write
---

Search for NYC apartments matching these criteria:
- **Unit**: 1BR + den/office (sometimes listed as "flex 2BR" or "1BR+den")
- **Rent**: Under $4,700/month
- **Required amenities**: floor-to-ceiling windows, in-unit washer/dryer, gym, parking for a car AND motorcycle
- **Preferred**: highrise, walk-in closet, balcony
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

4. Summarize findings: for each new candidate include:
   - Building name and address
   - Rent range for qualifying units
   - Which required amenities are confirmed vs unconfirmed
   - Parking situation (car + motorcycle — note if motorcycle parking is unclear)
   - Lifestyle amenities (write a brief paragraph noting): piano/music room, gym highlights (pool, climbing, basketball), co-working/business center
   - Any deal-breakers or notable pros/cons

5. Ask the user if they want to add any candidates to the relevant markdown file.
