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
