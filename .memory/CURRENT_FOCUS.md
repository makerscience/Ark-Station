# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. Playtest and balance gameplay

## Next Actions
- [ ] Playtest full game loop from intro to victory/defeat
- [ ] Balance decay/repair rates if game feels too fast or slow
- [ ] Consider adding display power cost mechanic (solar/orbital panels costing 1 power each)
- [ ] Add more variety to ending messages based on victory conditions

## Open Loops / Blockers
- Display power cost not yet implemented (plan mentioned it but skipped for now)

## How to Resume in 30 Seconds
- **Open:** `.memory/CURRENT_FOCUS.md`
- **Next:** Execute the first unchecked item in "Next Actions"
- **If unclear:** Run "Follow the Session Start Protocol"

## Key Context
- Memory files: `.memory/CURRENT_FOCUS.md`, `.memory/DECISIONS.md`
- Changelog: `CHANGELOG.md`
- How to start session: "Follow the Session Start Protocol"
- How to end session: "Do the Session End Protocol"
- Main game file: `index.html`
- Design document: `Ark Station — Crisis Management Survival Game Design Document.pdf`

---

## Last Session Summary (max ~8 bullets)
- Doubled all system decay rates and drone repair rates for faster-paced gameplay
- Fixed timer displays to show real seconds (was showing ticks as seconds)
- Added Emergency Override victory button - big red "EXECUTE" button appears when hacked
- Renamed "Research" → "Hack Systems" throughout UI for thematic consistency
- Locked drone repair targets (Thrusters/Shield) until those systems are unlocked
- Moved Skip button to bottom-right corner, made it 2x larger with flash animation
- Game now starts paused after intro - player must click START or a speed button
- Updated changelog with all session changes

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
