# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal NYC apartment hunting research repository. No build system, tests, or code — only Markdown documentation.

## Files

- `brooklyn_apartment_search.md` — Brooklyn candidates, parking research, ruled-out buildings
- `manhattan_apartment_search.md` — Manhattan candidates ranked by value/fit, parking strategy, priority call list
- `options/` — Dated snapshots from `/explore-my-options` runs (e.g., `2026-04-01-brooklyn-manhattan.md`)

## Skills

- `/search-apartments [area]` — Find new candidates in a neighborhood or research a specific building
- `/explore-my-options` — Fetch live StreetEasy listings and check each unit against criteria; saves results to `options/`

## Search Criteria

- 1BR + den/office, under $4,700/month
- Must have: floor-to-ceiling windows, in-unit W/D, gym, parking for both a car and motorcycle
- Highrise preferred; walk-in closet and balcony nice-to-have

## Conventions

Keep both files consistent in structure: active candidates with details → ruled-out buildings → parking notes → open questions/next steps.
