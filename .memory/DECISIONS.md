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

---

## 2026-01-27 (Session 4)
- Tags: architecture
- Decision: Shield flare protection changed from power-based reduction to integrity-tiered absorption.
- Rationale: Old system (power × integrity × 0.3, up to 90% reduction) made shield power the key variable. New tiered system (85%+ = 100% absorption, down to 0% at 0 integrity) makes shield integrity the key variable. Shield now takes 4× damage during flares (0.0888/tick), requiring active repair even at full power.
- Alternatives considered: Keep power-based system, hybrid power+integrity formula.
- Consequences / Follow-ups: Players must prioritize shield repair during flares. High integrity = full protection, degraded shield = increasing pass-through damage to reactor/stasis.

---

## 2026-01-27 (Session 4)
- Tags: architecture
- Decision: Orbital system unlocks pushed to later CA levels (CA5 for Orbital + Thrusters 1&2, CA6 for Thrusters 3&4). Hidden orbital decay starts at CA4 (was CA3).
- Rationale: Gives players more time to deal with solar flares before orbital crisis is revealed. Creates longer buildup before the "falling toward the sun" discovery moment.
- Alternatives considered: Keep at CA3/CA4, move even later.
- Consequences / Follow-ups: Orbital decay has more time to accumulate before player can see/counter it. May need tuning if orbit falls too far before unlocks.

---

## 2026-01-28
- Tags: architecture
- Decision: Orbital rebalancing - start at 50 (NEAR zone), 4x faster decay (0.01336/tick), 3 thrusters = stable, 4 = climbing.
- Rationale: Creates more urgency. Starting in the middle zone means players feel immediate tension when orbital status is revealed. 4x decay rate forces faster decision-making. Requiring 3 thrusters for stability (not 4) gives cleaner math and makes the 4th thruster feel like a meaningful upgrade for recovery.
- Alternatives considered: Keep original decay with just starting position change, require all 4 thrusters for stability.
- Consequences / Follow-ups: Players can now climb back to safety (cap at 100) with 4 thrusters. Balance may need adjustment if orbit falls too fast before CA5 unlocks.

---

## 2026-01-28 (Session 2)
- Tags: architecture
- Decision: 5-zone proximity system with zone-scaled mechanics.
- Rationale: Old 3-zone system (Far/Near/Critical at 66/33) was too coarse. New 5-zone system (Far/Medium/Close/Very Close/Critical at 80/60/40/20) enables finer-grained scaling of radiation damage (0.5x→6x), solar flare frequency/duration/damage, and visual intensity.
- Alternatives considered: Keep 3 zones with steeper curves, continuous scaling without discrete zones.
- Consequences / Follow-ups: All zone-dependent mechanics now share consistent boundaries. Shield provides partial protection (up to 50% reduction) but cannot fully block proximity effects.

---

## 2026-01-28 (Session 2)
- Tags: architecture
- Decision: Orbital distance progression through CA levels (CA2=90/FAR, CA3=70/MEDIUM, CA4=50/CLOSE).
- Rationale: Players experience each zone's ambient conditions (radiation, flares, visual effects) before orbital decay begins at CA4. Creates gradual escalation instead of sudden crisis reveal.
- Alternatives considered: Start at CA4 distance immediately, randomize starting distance.
- Consequences / Follow-ups: Research tree extended to 8 levels (Emergency Override at CA8). Thruster rebalanced: 2=stable, 3=climb, 4=fast climb for quicker endgame recovery.

---

## 2026-01-28 (Session 3)
- Tags: architecture
- Decision: Non-linear thruster contributions with 0.1/sec base decay.
- Rationale: Creates more dramatic tension. 1 thruster barely helps (0.07/sec fall), 2 thrusters almost stabilize (0.02/sec fall), 3 thrusters climb slowly (0.03/sec rise), 4 thrusters climb fast (0.10/sec rise). Each thruster feels meaningfully different.
- Alternatives considered: Linear contributions (each thruster = baseDecay/4).
- Consequences / Follow-ups: Faster base decay creates urgency. 2 thrusters is a meaningful milestone (almost stable). 4 thrusters can recover as fast as base decay.

---

## 2026-01-28 (Session 3)
- Tags: architecture
- Decision: Emergency Override (victory) locked until station reaches >40,000 km from Roche limit.
- Rationale: Forces players to stabilize orbit before winning. Can't just rush research while falling to destruction. Creates a two-phase endgame: first climb to safety, then hack victory.
- Alternatives considered: No distance requirement (original), require FAR zone (>80,000 km).
- Consequences / Follow-ups: Shows "Too Close to Roche Limit" message when locked. Players must use thrusters to escape Critical/Very Close zones before victory is possible.
