# Ark Station - Change Control Document

This document tracks all changes made to the project.

---

## [Unreleased]

### 2026-01-20 - Intro Sequence Overhaul
**Author:** Claude (AI Assistant)

#### Changed
- **Story intro now displays as cinematic text sequence:**
  - Black screen with paragraphs fading in one by one
  - 6 story paragraphs with ~10 seconds between each (60s total)
  - Text starts 15% from top of screen for better readability
  - Longer fade-in transitions (2s) for dramatic effect
- **Player controls the pacing:**
  - "SKIP" button in bottom-left to skip entire intro
  - "CONTINUE" button appears after all text, must click to proceed
  - No more auto-transition to reactor phase
- **Reactor phase is now separate screen:**
  - Only reactor button visible on black screen
  - Player clicks 10 times to initialize (unchanged)

#### Added
- New story paragraphs expanding the narrative (6 total, user-authored)
- Continue button with fade-in animation
- Scrollable story container for longer text

#### Notes
- Story timing: 4s, 14s, 24s, 34s, 44s, 54s for each paragraph
- Continue button appears at 60s
- All timers cleared properly on skip/continue/restart

---

### 2026-01-20 - Integrity-Based Scaling System
**Author:** Claude (AI Assistant)

#### Changed
- **Reactor power now scales with integrity:**
  - Formula: `basePower = floor((integrity / 20) * 5) + bonusPower`
  - Every 20% integrity = 5 base power
  - At 20%: 5 power, at 100%: 25 power
  - Power upgrades add bonus on top (+1 each, max +2)
- **All system effectiveness scales with integrity:**
  - Shield: `effectiveness = integrity / 20` (1x at 20%, 5x at 100%)
  - Thrusters: `effectiveness = integrity / 20` (1x at 20%, 5x at 100%)
  - Stasis: Higher integrity = lower death rate (up to 50% reduction)
- **Max integrity caps changed from 150% to 100%:**
  - Reinforcement I: 20% → 60% (capBonus 80 → 40)
  - Reinforcement II: 60% → 100% (capBonus 50 → 40)
  - Descriptions updated to reflect new caps

#### Added
- **Integrity bars now show locked portion:**
  - Bars are 3x longer (450px vs 150px)
  - Green/yellow/red fill shows current integrity
  - Dark gray section shows locked potential (100% - maxIntegrity)
  - Locked section shrinks as upgrades are purchased

#### Notes
- At game start: 20% of bar filled, 80% grayed out
- After Reinforcement I: up to 60% fillable, 40% grayed
- After Reinforcement II: full bar available (0% grayed)

---

### 2026-01-19 - System Integrity Cap Progression
**Author:** Claude (AI Assistant)

#### Changed
- **All systems now start at 20% max integrity**
  - Creates early-game challenge requiring quick research
  - Reactor at 20% provides only 1 power unit
- **Reinforcement I upgrades now unlock 100% max integrity** (was +20%)
  - capBonus changed from 20 to 80
  - Descriptions updated: "Unlock [system] potential (100% max integrity)"
- **Reinforcement II upgrades now unlock 150% max integrity** (was +30%)
  - capBonus changed from 30 to 50
  - Descriptions updated: "Enhance [system] beyond specs (150% max integrity)"

#### Notes
- Progression: 20% → 100% (Tier I) → 150% (Tier II)
- Final max integrity unchanged at 150%
- Early game is now much more challenging - research is critical for survival
- Reactor at 20% = 1 power, making Command Auth 2 a priority

---

### 2026-01-19 - Solar Storm Variation
**Author:** Claude (AI Assistant)

#### Changed
- Solar flares now have much greater timing variation
- Flare interval: 30 seconds to 4 minutes (was ~2 minutes fixed)
- Random timing each flare, making gameplay less predictable

#### Notes
- Range: 30-240 ticks (30s minimum, 240s maximum)
- Creates more tension as flares can come in quick succession or give long breaks

---

### 2026-01-19 - UI Layout Overhaul
**Author:** Claude (AI Assistant)

#### Changed
- **Two-column layout:**
  - Left column: Survivors (moved to top), Power Grid, Systems, Controls
  - Right column: Orbital Status, Solar Forecast
  - Responsive design collapses to single column on narrow screens
- **Survivors panel moved above Power Grid** for better visibility
- **Container width increased** from 600px to 900px to accommodate layout

#### Added
- **Orbital visualization graphic:**
  - Visual track showing Ark Station position relative to sun/Roche Limit
  - Animated sun glow on right side
  - Roche Limit marker line with label
  - Ark Station icon (green when safe, red/pulsing when critical)
  - Station position updates based on orbital distance value
  - Smooth transition animation as station moves

#### Notes
- Station visual position: 15% (far/safe) to 80% (at Roche Limit)
- Station turns red and pulses when distance < 33 (CRITICAL)

---

### 2026-01-19 - Research Tree Restructure
**Author:** Claude (AI Assistant)

#### Changed
- **Research system restructured as a tech tree:**
  - Each tier now gated by a Command Authorization upgrade
  - Player starts at Command Level 1 (was 2)
  - Must research "Command Authorization N" to unlock Level N upgrades
  - 6 new gate upgrades added (Command Authorization 2-7)
  - Visual tree structure with level headers
  - Gate upgrades highlighted with distinct styling and lock icon
  - Future levels shown as locked/dimmed until unlocked

#### Notes
- Gate upgrade costs: 5s (L2), 10s (L3), 15s (L4), 20s (L5), 25s (L6), 30s (L7)
- Progression: Research gate → unlock tier → research upgrades → research next gate
- Total research time increased but provides clearer progression path

---

### 2026-01-19 - Phase 7 Implementation
**Author:** Claude (AI Assistant)

#### Added
- **Phase 7 - Polish + Endgame:**
  - Intro sequence: Click reactor button 10 times to initialize and start game
  - Visual feedback during intro (button glow, progress percentage)
  - Cryo-Log: Scrolling death messages appear in Survivors panel
  - Death messages randomly generated from 8 templates
  - System status indicators on all systems (ONLINE/STRESSED/CRITICAL/OFFLINE)
  - Color-coded status based on integrity thresholds
  - Ending screen with multiple outcomes based on survivor percentage:
    - 90%+ survivors: "Mission Complete" (victory)
    - 50-89%: "Mission Complete" (partial victory)
    - 10-49%: "Pyrrhic Victory"
    - 1-9%: "Near Total Loss"
    - 0%: "Mission Failed"
  - Ending screen shows initial colonists, survivors, and survival rate
  - Restart button to play again (full state reset)

#### Changed
- `index.html` - Added Phase 7 features (~200 lines added, now ~1440 lines total)
- Game over now triggers ending overlay instead of just disabling buttons
- Orbital destruction now properly shows ending screen

#### Notes
- Cryo-log entries appear with 30% probability per tick when deaths occur
- System status thresholds: <25% = CRITICAL, <50% = STRESSED, 0% = OFFLINE
- Intro overlay hides 1.5 seconds after reactor reaches 100%

---

### 2026-01-19 - Phase 6 Implementation
**Author:** Claude (AI Assistant)

#### Added
- **Phase 6 - Research System:**
  - RESEARCH button opens Command Authorization modal
  - Command Level system (starts at Level 1, max Level 7)
  - 12 upgrades across 6 levels:
    - Level 2: Reactor/Stasis max integrity +20%
    - Level 3: +1 max power, Thrusters/Shield max integrity +20%
    - Level 4: Reactor/Stasis max integrity +30% more
    - Level 5: +1 max power, 50% faster drone repairs
    - Level 6: Thrusters/Shield max integrity +30% more
    - Level 7: Emergency Override (for endgame)
  - Research costs time (10-30 seconds per upgrade)
  - Research progress indicator below buttons
  - Level up when all upgrades at current level are purchased
  - Systems now have maxIntegrity caps that upgrades increase
  - Drones have configurable repairRate

#### Changed
- `index.html` - Added research system (~250 lines added, now ~1060 lines total)

#### Fixed
- Starting Command Level changed from 1 to 2 (Level 1 had no upgrades available)

#### Notes
- Purchasing research auto-unpauses the game
- Max integrity caps allow systems to exceed 100%
- With all upgrades: 7 max power, 150% max integrity, 1.2 repair rate

---

### 2026-01-19 - Balance Adjustments
**Author:** Claude (AI Assistant)

#### Changed
- Solar flares now occur every ~2 minutes (100-140 ticks) instead of every 20-40 seconds
- Initial flare countdown changed from 30s to 120s
- Reactor now outputs full power (5 units) at 90%+ integrity instead of only at 100%
- New power thresholds: 90%+=5, 70-89%=4, 50-69%=3, 30-49%=2, 0-29%=1

---

### 2026-01-19 - Phase 5 Implementation
**Author:** Claude (AI Assistant)

#### Added
- **Phase 5 - Solar Shield + Radiation Spikes:**
  - New Solar Forecast panel showing flare status and countdown
  - Status levels: CLEAR (>15s), WARNING (5-15s), IMMINENT (<5s), ACTIVE (flare in progress)
  - Visual feedback: blinking text during IMMINENT and ACTIVE states
  - Solar Shield Matrix system with integrity bar and power allocation
  - Solar flares deal 3% base damage to all systems per tick
  - Shield reduces flare damage: power × (integrity/100) × 0.3 reduction (up to 90%)
  - Shield takes extra 2% damage during flares (absorbing radiation)
  - Flares last 5-10 ticks, occur every 20-40 ticks
  - Drones can now target Shield for repair

#### Changed
- `index.html` - Added solar mechanics (~170 lines added, now ~780 lines total)

#### Notes
- With 3 power to shield at 100% integrity: 90% flare damage reduction (0.3% instead of 3%)
- Shield decays at 0.2% normally, +2% during flares
- Flares create crisis moments requiring quick power reallocation

---

### 2026-01-19 - Phase 4 Implementation
**Author:** Claude (AI Assistant)

#### Added
- **Phase 4 - Orbital Mechanics:**
  - New Orbital Status panel showing distance to Roche Limit
  - Distance levels: FAR (>66), NEAR (33-66), CRITICAL (<33)
  - Orbital decay rate display
  - Radiation warnings at NEAR and CRITICAL distances
  - Orbital Thrusters system with integrity bar and power allocation
  - Thrusters reduce orbital decay based on power and integrity
  - Radiation multiplier affects all system decay rates:
    - FAR: 1x (normal)
    - NEAR: 1.5x decay
    - CRITICAL: 2x decay
  - Station destruction when distance reaches 0
  - Drones can now target Thrusters for repair

#### Changed
- `index.html` - Added orbital mechanics (~150 lines added, now ~610 lines total)

#### Notes
- Base orbital decay: 0.5 per tick
- Thruster effect: power × (integrity/100) × 0.3 reduction per tick
- At 2 power with 100% thrusters: decay reduced to 0.5 - 0.6 = stabilized
- Thrusters decay at 0.2% per tick (slower than other systems)

---

### 2026-01-19 - Phase 3 Implementation
**Author:** Claude (AI Assistant)

#### Added
- **Phase 3 - Repair Drones:**
  - New Repair Drones system with power allocation controls
  - Target selection UI (Reactor / Stasis buttons)
  - Visual feedback: "[REPAIRING]" indicator on targeted system
  - Repair rate: 0.8% integrity per power unit per tick
  - When power decreases, drones lose power first (before stasis)

#### Changed
- `index.html` - Added drones system (~100 lines added, now ~455 lines total)

#### Notes
- At 1 power to drones: +0.8% repair vs -0.3% reactor decay = net +0.5%/tick on reactor
- At 1 power to drones: +0.8% repair vs -0.5% stasis decay = net +0.3%/tick on stasis
- Players can now sustain systems indefinitely with proper power allocation

---

### 2026-01-19 - Phase 1 & 2 Implementation
**Author:** Claude (AI Assistant)

#### Added
- Created `index.html` - Single-file game with HTML, CSS, and JavaScript
- **Phase 1 - Core Loop:**
  - Dark terminal aesthetic UI
  - Power Grid display (allocated / total)
  - Survivor count with death rate indicator
  - Stasis Pod Life Support system with integrity bar
  - Power allocation controls ([+] / [-] buttons)
  - Start/Pause button
  - Game loop running at 1 tick per second
  - Death rate calculation based on power allocation and stasis integrity
  - Game over state when all survivors die

- **Phase 2 - Reactor Core:**
  - Reactor Core system with integrity bar
  - Reactor decays at 0.3% per tick
  - Total power output scales with reactor integrity (100% = 5 power, 20% = 1 power)
  - Auto-reduces power allocations when available power decreases
  - Visual feedback: integrity bars change color (green → yellow → red)

#### Files
- `index.html` (new) - ~345 lines

#### Notes
- Stasis integrity decays at 0.5% per tick
- Death rate formula: `baseDeaths * powerFactor * integrityFactor`
- Power provides up to 70% death rate reduction
- Integrity provides up to 50% death rate reduction

---

### 2026-01-19 - Repository Initialization
**Author:** Claude (AI Assistant)

#### Added
- Initialized git repository
- Connected to remote: https://github.com/makerscience/Ark-Station.git
- Created this CHANGELOG.md file

#### Notes
- Project started with game design document: "Ark Station — Crisis Management Simulator Game Design Document.pdf"

---

## Change Log Format

Each entry should follow this format:

```
## [Version or Date]

### Category (Added/Changed/Removed/Fixed)
- Description of change
- File(s) affected: `filename.ext`
- Reason for change (if applicable)
```

### Categories
- **Added**: New files, features, or functionality
- **Changed**: Modifications to existing files or features
- **Removed**: Deleted files or removed functionality
- **Fixed**: Bug fixes or corrections
