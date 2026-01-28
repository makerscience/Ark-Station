# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. Playtest and balance gameplay

## Next Actions
- [x] Add visual foreshadowing for Roche limit approach (red vignette + warning messages)
- [ ] Playtest full game loop from intro to victory/defeat
- [ ] Balance decay/repair rates if game feels too fast or slow
- [ ] Add scientific names for shield repair upgrades (currently placeholders)
- [ ] Add more variety to ending messages based on victory conditions
- [ ] Consider individual drone assignment system (explored but deferred)

## Open Loops / Blockers
- **Uncommitted changes pending playtest:** CA gate reordering (upgrades now at bottom of each level)
- Shield repair upgrades have placeholder names ("Solar Shield: Repair Enhancement I/II/III")
- Display power cost for solar/orbital panels not implemented

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
- Added Roche limit visual foreshadowing (red vignette overlay)
  - Activates at CA4, intensity scales with distance (0 at 66+ → 1.0 at 0)
  - Pulses when in CRITICAL zone (≤33), uses `mix-blend-mode: multiply`
- Added ambient warning messages before orbital panel unlocks:
  - Distance ≤40: thermal anomaly, ≤25: hull stress, ≤15: gravitational anomaly
- New helper `getRocheIntensity()` at line 4762
- New state `gameState.rocheWarnings` for one-time message triggers

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
