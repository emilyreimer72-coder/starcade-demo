# Starcade preview — calendar and metrics integrity (2026-10-11)

Scope: public `starcade-demo/preview.html` only. This is a design preview, not the live app. No changes to saved habits, star balances, Oura, or production deployment are authorized here.

## Verified issues on main
- Home date is hardcoded to Thursday, October 8.
- "This week" is generated from static weekday letters and dates 2–8, not the current week.
- October grid renders dates 1–31 in order without the required weekday offset (October 1, 2026 is Thursday).
- Progress shows a fabricated 8-day streak; sample star balance (145) is not clearly identified as sample data.
- Scratch-off says "You found 5 stars" without crediting a balance; the treasure chest likewise has only a visual preview interaction.

## Reversible implementation proposal
1. Render today's date, the current seven-day week, and the correct month from local `Date` values, with weekday headings, blank leading calendar cells, and a gold outlined today.
2. Label progress and reward balances as sample-only; replace the unconnected streak with an em dash. Never invent historical habit completion.
3. Keep preview chest and scratch-off as non-awarding interactions; do not claim real star awards.
4. Preserve five navigation buttons and all demo-only interactions. Do not touch persistent storage, network requests, or Oura integrations.
5. Validate calendar placement for 2026-10-01 (Thursday), 31 October dates, mobile widths 360/390/430px, screen-reader labels, and all five tabs.

## Validation and release
A proposed isolated HTML transformation passed JavaScript syntax validation and 13/13 targeted static checks before commit. The connector blocked the HTML file update; **the proposal is not committed or deployed**. This document records the actionable handoff only. Re-run tests and visually inspect the actual committed code before any merge or release.

Related production blocker: `starcade` PR #10 (illustrated Rewards) reports `mergeable=false`; resolve conflicts and verify CI separately before merging.
