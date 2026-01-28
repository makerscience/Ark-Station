# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. Playtest and balance gameplay

## Next Actions
- [ ] Playtest full game loop from intro to victory/defeat
- [ ] Balance decay/repair rates if game feels too fast or slow
- [ ] Add scientific names for shield repair upgrades (currently placeholders)
- [ ] Add more variety to ending messages based on victory conditions
- [ ] Consider individual drone assignment system (explored but deferred)

## Open Loops / Blockers
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
- Non-linear thruster mechanics: base 0.1/sec decay, 1T=0.07↓, 2T=0.02↓, 3T=0.03↑, 4T=0.10↑
- Death rate shows "STABILIZED" (green) when at zero
- HACK SYSTEMS button locks during research, shows "HACKING {name}..." in smaller font
- Start/Pause locked during solar flares, shows "ERROR" in red
- Orbital distance shows zone + km (e.g., "FAR — 90,000 km")
- Shield panel shows blocking % and radiation warning (5 levels + flare max)
- Emergency Override locked until station climbs above 40,000 km
- Removed ambient temperature display (replaced by radiation warning)

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
