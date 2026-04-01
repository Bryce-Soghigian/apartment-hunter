---
name: explore-my-options
description: Fetch live StreetEasy listings for all active apartment candidates and check each unit against the search criteria. Use when the user wants to see which specific units are available right now and whether they actually qualify.
user-invocable: true
allowed-tools: Read, Write, Bash, WebSearch, WebFetch
---

You are checking live apartment listings against the search criteria. Be thorough — fetch actual listing pages, not just search results.

## Search Criteria (hard requirements)

- **Rent**: ≤$4,700/mo effective (gross up to ~$5,069/mo qualifies if 1 month free on 14-month lease)
- **Unit type**: 1BR + den/office, OR 2BR
- **Windows**: Floor-to-ceiling (required)
- **Laundry**: In-unit washer/dryer (required)
- **Gym**: In building (required)
- **Parking**: On-site (required)

Nice-to-have: highrise, walk-in closet, balcony.

## Steps

1. Read `brooklyn_apartment_search.md` and `manhattan_apartment_search.md` to get the list of active (non-ruled-out) candidates and any known StreetEasy URLs.

2. For each active building:
   a. If you don't already have a StreetEasy building URL, search for one: `site:streeteasy.com "[Building Name]" rentals`
   b. WebFetch the StreetEasy building page to get the list of currently available units and their prices
   c. For each available unit that looks like it could be a 1BR+den or 2BR and is in the price range, note the unit number, price, beds/baths, and any listed features

3. Cross-check each candidate unit against the hard requirements. Mark each as:
   - ✅ PASS — meets all hard requirements
   - ⚠️ POSSIBLE — meets most but one or more requirements are unconfirmed (e.g. den layout not listed)
   - ❌ FAIL — definitively doesn't meet a hard requirement (over budget, no parking, etc.)

## Output Format

Group by borough. For each building show only units that PASS or are POSSIBLE — skip buildings with no qualifying units entirely.

**Building Name** — Neighborhood
| Unit | Price | Beds | Status | Link | Notes |
|---|---|---|---|---|---|
| #XYZ | $X,XXX/mo | 1BR+den | ✅ PASS | [View](https://streeteasy.com/building/building-name/xyz) | Balcony, walk-in closet |
| #ABC | $X,XXX/mo | 2BR | ⚠️ POSSIBLE | [View](https://streeteasy.com/building/building-name/abc) | Den unconfirmed |

- StreetEasy: [link]

At the end: summary count of PASS units, POSSIBLE units, and buildings with nothing available.

## Building Notes

For each building, include a brief paragraph right after the unit table and bullet points summarizing lifestyle amenities you found (major pluses to call out):

- **Piano / Music Room**
- **Gym Highlights** — Pool, rock climbing, basketball, sauna, etc.
- **Co-working** — Business center, library lounge, shared workspace

Only mention amenities you have confirmed information about. Do not mention unknowns or "call to confirm" — this report is for what we know now.

Example format:

**Building Name** — Neighborhood
| Unit | Price | Beds | Status | Link | Notes |
|---|---|---|---|---|---|
| #XYZ | $X,XXX/mo | 1BR+den | ✅ PASS | [View](url) | Balcony |

- StreetEasy: [link]

> Gym features a rock climbing wall, cold plunge, and sauna. Has a library lounge for co-working.

## Save Results

After generating the report, save it to the `options/` directory:

1. Create the directory if it doesn't exist: `mkdir -p options/`
2. Save the report as `options/{YYYY-MM-DD}-{neighborhoods}.md`
   - Use today's date
   - List neighborhoods covered, lowercase, hyphenated (e.g., `2026-04-01-brooklyn-manhattan.md` or `2026-04-15-hudson-yards-hells-kitchen.md`)
   - If searching all boroughs, just use `brooklyn-manhattan`
3. Include the date and neighborhoods at the top of the saved file
