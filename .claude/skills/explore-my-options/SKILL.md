---
name: explore-my-options
description: Fetch live StreetEasy listings for all active apartment candidates and check each unit against the search criteria. Use when the user wants to see which specific units are available right now and whether they actually qualify.
user-invocable: true
allowed-tools: Read, WebSearch, WebFetch
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
| Unit | Price | Beds | Status | Notes |
|---|---|---|---|---|
| #XYZ | $X,XXX/mo | 1BR+den | ✅ PASS | Balcony, walk-in closet |
| #ABC | $X,XXX/mo | 2BR | ⚠️ POSSIBLE | Den unconfirmed, parking unconfirmed |

- StreetEasy: [link]

At the end: summary count of PASS units, POSSIBLE units, and buildings with nothing available.
