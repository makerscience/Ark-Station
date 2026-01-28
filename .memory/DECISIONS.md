# DECISIONS

Format:
- Date:
- Tags: (workflow, architecture, tooling, convention, failure-mode)
- Decision:
- Rationale:
- Alternatives considered:
- Consequences / Follow-ups:

---

## 2026-01-24
- Tags: architecture, workflow
- Decision: Governance-only memory (no MCP server) using CLAUDE.md + .memory files.
- Rationale: Minimum complexity while maintaining continuity across sessions.
- Alternatives considered: Full MCP project-memory server with ChromaDB.
- Consequences / Follow-ups: If memory friction grows, revisit adding MCP later.

Tip: Search with `rg "Tags:.*workflow" .memory/DECISIONS.md`

---

## 2026-01-26
- Tags: architecture
- Decision: 5-phase progression system with hidden mechanics and progressive UI reveals.
- Rationale: Creates dramatic tension by hiding solar flares (until CA2) and orbital decay (until CA3). Player discovers systems are failing before they can see why.
- Alternatives considered: All systems visible from start (original), instant unlocks without discovery.
- Consequences / Follow-ups: May need balancing if early phases feel too easy or discovery is too punishing.

---

## 2026-01-27
- Tags: architecture
- Decision: Simplified reactor power formula - 1 power per 4% integrity using ceil(), removed Reactor Power Upgrades.
- Rationale: Old formula (floor(integrity/20)*5 + bonus) dropped power immediately at game start. New formula (ceil(integrity/4)) gives 3% buffer before first power loss at 20% starting integrity. Power upgrades were redundant since power scales naturally with reactor reinforcement.
- Alternatives considered: Keep power upgrades with adjusted formula, use round() instead of ceil().
- Consequences / Follow-ups: Max power now 25 (at 100% integrity) instead of variable based on upgrades. Reactor Reinforcement upgrades are now the sole path to more power.

---

## 2026-01-27 (Session 2)
- Tags: architecture
- Decision: Independent unlock for subsystems within panels (Solar/Shield, Orbital/Thrusters).
- Rationale: Players may want to unlock shield before seeing solar forecast, or thrusters before orbital status. Each subsystem now has its own "System Offline" indicator and can be researched independently.
- Alternatives considered: Keep paired unlocks (solar always comes with shield visibility).
- Consequences / Follow-ups: More flexible research paths. UI shows each subsystem's ONLINE/OFFLINE status separately.

---

## 2026-01-27 (Session 2)
- Tags: architecture
- Decision: Shield has no integrity cap upgrades - starts at 3% integrity with 100% max. Shield upgrades boost drone repair speed instead.
- Rationale: Shield is different from other systems - it should be repairable to full from the start but is fragile and slow to repair. Makes shield management more about prioritization than upgrade gating.
- Alternatives considered: Keep 4-tier integrity cap upgrades like other systems.
- Consequences / Follow-ups: Shield repair multiplier goes 1.0x → 1.5x → 2.0x → 2.5x with 3 upgrades. Players need to balance drone time between shield and other systems.

---

## 2026-01-27 (Session 2)
- Tags: architecture
- Decision: Reactor power formula changed to 1 power per 5% integrity (max 20, was max 25).
- Rationale: User requested each reactor upgrade add 4 power capacity for cleaner progression. At 20% integrity = 4 power, each +20% integrity upgrade adds 4 power, max 20 power at 100%.
- Alternatives considered: Keep 1 per 4% (max 25).
- Consequences / Follow-ups: Slightly tighter power budget. Game may need rebalancing.

---

## 2026-01-27 (Session 3)
- Tags: architecture
- Decision: Thrusters converted from single integrity-based system to 4 individual binary units.
- Rationale: Removes complexity of thruster integrity/repair. Each thruster is a simple on/off toggle that consumes 1 power. Unlocked progressively via research (T1 with panel, T2-T4 as separate upgrades at L4/L5/L6). 4 thrusters = stable orbit.
- Alternatives considered: Keep integrity system with repair, variable power consumption per thruster.
- Consequences / Follow-ups: Thrusters removed from drone repair targets. Simpler mental model for players. Orbital decay formula simplified (each thruster = 0.001 reduction vs 0.00334 base).
