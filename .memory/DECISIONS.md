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
