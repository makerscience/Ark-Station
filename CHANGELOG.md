# Ark Station - Change Control Document

This document tracks all changes made to the project.

---

## [Unreleased]

### 2026-01-27 - UI Layout Overhaul and Reactor Power Changes
**Author:** Claude (AI Assistant)

#### Added
- **Casualty Log panel at bottom of screen:**
  - Full-width horizontal panel below main game area
  - Deaths display as cards in a scrollable row (newest on left)
  - "POD FAILURE" displayed on its own line in each card
  - Red-themed styling with custom scrollbar
- **Locked panel placeholders:**
  - Offline systems (Drones, Orbital, Solar) now visible from game start
  - Show panel title with "⚠ System Offline" indicator
  - Panels dimmed at 50% opacity until unlocked
  - Gives players sense of final layout without revealing details

#### Changed
- **New reactor power formula:** Every 4% integrity = 1 power
  - Power increases at 5%, 9%, 13%, 17%, etc. (bottom of each 4% bracket)
  - At 20% integrity: 5 power (starting value)
  - At 100% integrity: 25 power (maximum)
  - Power won't drop until integrity falls below 17% (3% buffer from start)
- **Removed all 5 Reactor Power Upgrades** (power_1 through power_5)
  - Power now scales purely with reactor integrity
  - Simplifies progression - focus on reactor reinforcement to unlock more power
- **Reactor Core visual redesigned:**
  - Visual enlarged ~75% (container 120px → 210px)
  - Centered in panel with info section below instead of beside
  - Power display increased to 36px font
  - Integrity bar centered with max-width constraint
- **Repair Drones panel moved to center column:**
  - Now positioned above Reactor Core panel
  - Left sidebar contains only Stasis Bay
- **Speed controls moved to right side of header:**
  - Game clock on left, title centered, speed controls on right
  - Speed indicator positioned next to speed buttons
- **Brightened all grey UI text for readability:**
  - #444 → #777, #555 → #888, #666 → #999, #888 → #aaa
- **Game now stays paused during intro sequence:**
  - Time no longer passes while intro text displays
  - Player must click START or a speed button after intro to begin
- **Life Support power bar repositioned:**
  - Moved from ship visual to directly above +/- controls
  - Renamed label to "Life Support Power"

#### Notes
- Max potential display updates dynamically based on reactor max integrity
- Formula: `Math.max(1, Math.ceil(integrity / 4))`

---

### 2026-01-26 - Emergency Override Victory Button
**Author:** Claude (AI Assistant)

#### Added
- **Emergency Override button for game victory:**
  - Large red circular button appears when Emergency Override is hacked
  - Centered on screen with pulsing "Emergency Override Ready" label
  - Clicking "EXECUTE" triggers the victory ending
  - Button properly resets on game restart

#### Notes
- Fixes issue where game wasn't ending when Emergency Override was researched
- Provides satisfying climactic moment for victory condition

---

### 2026-01-26 - Timer Display Fixes
**Author:** Claude (AI Assistant)

#### Fixed
- **All timer displays now show real seconds (were showing ticks):**
  - Solar forecast countdown: divided by 5 to convert ticks to seconds
  - Solar flare duration: divided by 5
  - Research progress indicator: divided by 5
  - Upgrade costs in System Access window: divided by 5

#### Notes
- At 5 ticks/second, raw tick values were 5x larger than real seconds
- Displays now accurately reflect real-time durations

---

### 2026-01-26 - Faster Decay and Repair Rates
**Author:** Claude (AI Assistant)

#### Changed
- **All system integrity decay rates doubled for faster-paced gameplay:**
  - Reactor: 0.00111% → 0.00222% per tick
  - Stasis: 0.00167% → 0.00334% per tick
  - Thrusters: 0.00078% → 0.00156% per tick
  - Shield: 0.00078% → 0.00156% per tick
  - Orbital decay: 0.00167 → 0.00334 per tick
- **Drone repair rate doubled to match:** 0.00887 → 0.01774 per tick
- **Thruster effect doubled to maintain orbital balance:** 0.000667 → 0.001334

#### Notes
- Game now has more urgency - systems degrade faster
- Balance maintained: repair drones are equally more effective
- Orbital mechanics unchanged in relative difficulty

---

### 2026-01-26 - UI Polish and Locked Drone Targets
**Author:** Claude (AI Assistant)

#### Changed
- **Renamed "Research" to "Hack Systems" throughout UI:**
  - Button changed from "RESEARCH" to "HACK SYSTEMS"
  - Modal title changed from "COMMAND AUTHORIZATION" to "SYSTEM ACCESS"
  - "Current Level" changed to "Access Level"
  - Individual upgrade buttons changed from "RESEARCH" to "HACK"
  - Progress indicator shows "Hacking..." instead of "Researching..."
- **Drone repair targets now properly locked until systems unlocked:**
  - Thrusters and Shield targets hidden in drone visual until researched
  - Target buttons also hidden until corresponding system unlocked
- **Simplified death rate formula:** smooth curve based on (power/5) * min(1, integrity/95)

---

### 2026-01-26 - Phase-Based Game Progression System
**Author:** Claude (AI Assistant)

#### Added
- **5-phase progression system tied to Command Authorization levels:**
  - Phase 1 (CA1): Stasis pods only - players learn death rate management
  - Phase 2 (CA2): Repair Drones unlocked - solar flares begin dealing hidden damage
  - Phase 3 (CA3): Solar Forecast & Shield unlocked - orbital decay begins (hidden)
  - Phase 4 (CA4): Orbital Status & Thrusters unlocked - players discover station falling
  - Phase 5 (CA5+): All systems visible, race to Emergency Override victory

- **32 research upgrades (up from 16):**
  - System unlock upgrades: Repair Drones, Solar Forecast, Solar Shield Matrix, Orbital Status, Orbital Thrusters
  - Power progression: 5→8→11→14→17→20 via 5 reactor upgrades (+3 each)
  - 4-tier reinforcement for each system (20%→40%→60%→80%→100%)

- **Orbital movement indicator:**
  - Shows direction: ↑ climbing, ↓ falling, — STABLE
  - Shows speed in units per second
  - Color-coded: green for climbing, red for falling

- **UI visibility system:**
  - Panels hidden until researched with `.locked` CSS class
  - Drones panel, Solar panel, Shield controls, Orbital panel, Thruster controls all gated

#### Changed
- **Solar flare timing reduced to 2-4 minutes (was 4.5-36 minutes)**
- **Power caps added to all systems (5 each):** drones, shield, thrusters now capped like stasis
- **Solar flares only deal damage after CA Level 2**
- **Orbital decay only active after CA Level 3**
- **Renamed "Orbital Decay" display to "Movement" with directional indicators**

#### Notes
- Hidden mechanics create dramatic tension - players see damage before they understand the source
- Discovery moments when unlocking Solar Forecast (see flares) and Orbital Status (see station falling)
- Plan mentioned display power costs (1 power each for Solar/Orbital panels) - not yet implemented

---

### 2026-01-26 - Tick Rate Increase for Smoother Gameplay
**Author:** Claude (AI Assistant)

#### Changed
- **Tick rate increased from 3000ms to 200ms (5 ticks/second):**
  - Game now updates 15x more frequently for smoother, more responsive feel
  - All per-tick rates divided by 15 to maintain same real-time pacing
  - All tick counts multiplied by 15 (research costs, flare timing)

- **Decay rates adjusted (all ÷15):**
  - Reactor: 0.0167% → 0.00111%
  - Stasis: 0.025% → 0.00167%
  - Thrusters: 0.0117% → 0.00078%
  - Shield: 0.0117% → 0.00078%
  - Orbital: 0.025 → 0.00167
  - Thruster effect: 0.01 → 0.000667

- **Combat/repair rates adjusted (all ÷15):**
  - Base flare damage: 0.5 → 0.0333
  - Shield flare damage: 0.333 → 0.0222
  - Base death rate: 0.833 → 0.0556
  - Drone repair rate: 0.133 → 0.00887
  - Drone Efficiency upgrade: 0.067 → 0.00447

- **Research costs adjusted (all ×15):**
  - 5 → 75, 10 → 150, 12 → 180, 15 → 225, 20 → 300, 25 → 375, 30 → 450

- **Solar flare timing adjusted (all ×15):**
  - Initial flare: 90-720 → 1350-10800 ticks
  - Post-flare cooldown: 30-240 → 450-3600 ticks
  - Flare duration: 5-10 → 75-150 ticks

#### Notes
- Same overall game duration and balance maintained
- UI now feels significantly more responsive
- Game clock still advances at same real-time rate

---

### 2026-01-26 - Stasis Bay Death Rate Display Overhaul
**Author:** Claude (AI Assistant)

#### Changed
- **Death rate display now always visible:**
  - Shows "−X.X/sec" format instead of occasional "−1 per cycle"
  - Updates in real-time as power/integrity changes
  - Displays projected rate even when paused (for planning)

- **Stasis bay power capped at 5:**
  - New constant MAX_STASIS_POWER = 5
  - Power allocation formula now uses this cap instead of maxPower
  - Allows for more predictable death rate scaling

- **Death rate rebalanced:**
  - Base deaths increased to 0.741 per tick (from 0.0556)
  - At 5 power + 20% integrity = exactly 1 death/sec
  - Gives players clearer feedback on life support effectiveness

#### Notes
- Death rate is calculated in both updateUI() and gameTick()
- This ensures the display updates immediately when power changes

---

### 2026-01-25 - Passenger Death Records Integration
**Author:** Claude (AI Assistant)

#### Added
- **PASSENGER_DATABASE constant with 1200+ unique passengers:**
  - Each entry has name, age, and specialization
  - Data sourced from "Ark Station death record.csv"
  - Wide variety of sci-fi job titles (Quantum Consciousness Researcher, Void Meditation Instructor, etc.)
  - Includes children (age 2-14) with "Child" specialization
  - Ages range from 2 to 95

- **Passenger queue system for death messages:**
  - `passengerQueue` array stores shuffled indices
  - `passengerIndex` tracks current position
  - Fisher-Yates shuffle ensures random order each game
  - Queue wraps around if exhausted (unlikely with 1200+ passengers)

- **`initPassengerQueue()` function:**
  - Creates and shuffles passenger index array
  - Called from `initStasisGrid()` on new game and restart

#### Changed
- **Cryo-log death messages now show real passenger data:**
  - Format: "Name (Age), Specialization - Pod failure"
  - Example: "Eduardo Chávez (59), Shuttle Pilot - Pod failure"
  - Every tick with deaths shows one passenger (was 30% chance)
  - Replaced generic `generateDeathMessage()` with `getNextPassengerDeath()`

- **Cryo-log CSS adjustments:**
  - Increased max-height from 120px to 180px for vertical layout
  - Added word-wrap: break-word for long specialization names

#### Notes
- Old `DEATH_MESSAGES` constant and `generateDeathMessage()` removed
- Each game session shows passengers in different random order
- Adds emotional weight to deaths - they're no longer just numbers

---

### 2026-01-24 - Game Clock and Slower Tick Rate
**Author:** Claude (AI Assistant)

#### Added
- **Game clock display in top-left corner:**
  - Shows "Month Day, HH:MM, Year" format (e.g., "October 17, 00:00, 3326")
  - Game starts at October 17, 00:00, 3326
  - Each tick advances 10 minutes of game time
  - Clock rolls over correctly (23:50 → 00:00, day increments)
  - Uses 30-day months for simplicity
  - Clock resets on game restart

#### Changed
- **Game tick rate slowed from 1 second to 10 seconds:**
  - Creates more deliberate, strategic pacing
  - Each tick now represents 10 minutes of in-game time
  - All decay/damage/repair rates reduced by 6x to maintain same real-time gameplay speed
- **Rate adjustments (all ÷6 to match 6x fewer ticks per game-hour):**
  - Reactor decay: 0.1% → 0.0167%
  - Stasis decay: 0.15% → 0.025%
  - Thrusters decay: 0.07% → 0.0117%
  - Shield decay: 0.07% → 0.0117%
  - Flare damage: 3% → 0.5%
  - Shield extra flare damage: 2% → 0.333%
  - Orbital decay: 0.15 → 0.025
  - Thruster effect: 0.06 → 0.01
  - Repair rate: 0.8 → 0.133
  - Base deaths: 5 → 0.833 (with fractional accumulation)
  - Drone Efficiency upgrade boost: 0.5 → 0.067

#### Notes
- Clock positioned absolutely in top-left of container
- Uses monospace font with green glow to match terminal aesthetic
- gameState now includes gameTime object tracking minute, hour, day, month, year
- Added fractionalDeaths accumulator to handle sub-integer death calculations

---

### 2026-01-20 - Repair Drones Panel Redesign
**Author:** Claude (AI Assistant)

#### Changed
- **Systems panel renamed to "Repair Drones" panel with visual graphics:**
  - Central drone hub with up to 5 animated drones
  - 4 target system icons in corners:
    - **Reactor**: Orange glowing core with containment ring
    - **Stasis**: Three green stasis pods
    - **Thrusters**: Engine body with exhaust flame
    - **Shield**: Two cyan arc barriers
  - Drones fly all the way from hub to active target icon with staggered timing
  - Active target highlighted and pulsing when being repaired

#### Visual Feedback Based on Power Level
- **Power 0**: No drones visible
- **Power 1**: 1 drone flying to target
- **Power 2**: 2 drones flying to target
- **Power 3-4**: 3-4 drones flying to target
- **Power 5**: All 5 drones flying to target with full swarm effect

#### Notes
- All animations use CSS for performance
- Drone positions staggered to create swarm effect
- Target icons use same visual language as main system panels
- Inactive targets dimmed to emphasize current repair focus

---

### 2026-01-20 - Solar Forecast Panel Enhancement
**Author:** Claude (AI Assistant)

#### Added
- **Solar Forecast panel now has animated sun graphic:**
  - Sun core with corona and 8 radiating rays
  - 4 visual states matching forecast status:
    - **CLEAR**: Calm orange sun with slow 4-second pulse
    - **WARNING**: Brighter sun, corona expands, 2-second pulse
    - **IMMINENT**: White-hot core, rays become visible, rapid 0.5-second pulse
    - **ACTIVE**: Maximum intensity with rotating rays and flare burst animation
  - Flare burst element that animates outward during active state
  - Background shows deep space gradient

- **Solar Shield Matrix integrated into Solar Forecast panel:**
  - Shield visual graphic with 5 concentric arcs
  - Arcs light up progressively based on power allocation (1-5 levels)
  - Floating energy particles appear at power level 3+
  - "Absorbing" effect during active solar flares (arcs glow orange)
  - Impact glow effect when shield is absorbing flare damage
  - Power level 5 has continuous pulse animation
  - Power controls, integrity bar, and status moved into panel

#### Removed
- Solar Shield Matrix entry from Systems panel (consolidated into Solar Forecast)

#### Fixed
- JavaScript error where `shield` variable was used before being defined in updateUI()
- This bug caused all game controls (start button, power buttons) to stop working

#### Notes
- All animations are CSS-only for performance
- Shield visual positioned at bottom of solar graphic area
- Shield arcs create protective barrier effect between sun and bottom of view
- "Absorbing" state provides visual feedback when shield is actively protecting
- Complements existing sun animation to show the defensive relationship

---

### 2026-01-20 - Orbital Status Panel Enhancement
**Author:** Claude (AI Assistant)

#### Changed
- **Orbital Thrusters integrated into Orbital Status panel:**
  - Thruster visual graphic with animated firing effect
  - Flame intensity scales with power allocation (5 levels)
  - Level 1-2: Small blue flame with subtle flicker
  - Level 3-4: Larger flame with faster animation
  - Level 5: White-hot core with intense pulsing flame
  - Power controls, integrity bar, and status moved into panel
  - Thruster graphic positioned next to orbital visualization

#### Removed
- Orbital Thrusters entry from Systems panel (consolidated into Orbital Status)

#### Notes
- Flame uses CSS-only animation for performance
- Outer flame provides glow effect, inner flame shows core
- Visual feedback helps players understand thruster power allocation
- Panel now shows complete orbital management: position, decay, and thrust control

---

### 2026-01-20 - Ark Ship Survivors Panel Redesign
**Author:** Claude (AI Assistant)

#### Changed
- **Survivors panel completely redesigned as "Ark Ship — Stasis Bay":**
  - Visual Ark Ship with CSS-based hull, pod grid, and engine section
  - 32-pod grid (4x8) representing stasis pods - pods light up green when active, turn dark red as survivors die
  - Pod grid updates proportionally based on survivor percentage
  - Engine glow effect activates when power is allocated to life support
  - Power indicator bar below ship shows current life support power allocation
  - Survivor count now much larger (56px font) with dynamic coloring:
    - Green: Normal (>50% survivors)
    - Orange/Warning: Below 50% survivors
    - Red/Pulsing: Below 30% survivors (critical)
- **Stasis Pod Life Support controls integrated into Survivors panel:**
  - Power controls ([−] / [+]) moved into panel
  - Integrity bar and status indicator included
  - Cleaner "Life Support System" header

#### Removed
- Stasis Pod Life Support entry from Systems panel (consolidated into Ark Ship panel)

#### Notes
- Pod grid uses 32 visual pods to represent ~10,000 colonists (each pod ≈ 312 survivors)
- Engine glow has pulsing animation when powered
- Panel positioned on left side of screen for prominence
- Survivor count pulses when critical to draw attention

---

### 2026-01-20 - Reactor Core Visual Redesign
**Author:** Claude (AI Assistant)

#### Changed
- **Power Grid panel redesigned as "Reactor Core" panel:**
  - Visual reactor core with dynamic glow effect
  - Five concentric containment rings corresponding to integrity levels (20%, 40%, 60%, 80%, 100%)
  - Reactor core expands outward as integrity increases, filling more rings
  - Rings light up when integrity reaches their threshold
  - Rings glow brighter ("powered") when power output reaches corresponding level
  - Glow intensity scales with current power output (1-27 range, 5 glow levels)
  - Inner core brightness also scales with power
  - At max power (27), reactor pulses with intense glow animation
- **Reactor system info moved into Reactor Core panel:**
  - Power display shows Allocated / Output
  - Max Potential indicator (27 power)
  - Integrity bar with locked section
  - Status indicator (CRITICAL/STRESSED/ONLINE)
  - Repairing indicator when drones target reactor

#### Removed
- Reactor Core entry from Systems panel (consolidated into new panel)

#### Notes
- Ring thresholds: Ring 1 at 20%, Ring 2 at 40%, Ring 3 at 60%, Ring 4 at 80%, Ring 5 at 100%
- Reactor core sizes: 30px (20%), 50px (40%), 70px (60%), 90px (80%), 110px (100%)
- Glow levels: 0 (dim) at 1-5 power, up to 5 (intense pulsing) at 23-27 power
- Rings become "powered" when power reaches 5, 10, 15, 20, 25 respectively
- Inner core opacity ranges from 20% to 100% based on power

---

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
- Bright green pulse animation on reactor button clicks during startup
  - Massive pulses expand to 2500% size (10x larger than original)
  - Pulse intensity scales from 30% to 100% as clicks progress
  - Final click has special slower pulse (1.2s) that expands to 4000% with white-hot center
  - Final pulse ripples out, then triggers full-screen flash that fades to reveal the game UI

#### Notes
- Story timing: P1 at 1.5s, P2 at 10s, P3 at 32s, P4 at 47s, P5 at 59s, P6 at 71s
- Gaps: P1 fast, then 8.5s, 22s, 15s, 12s, 12s between paragraphs
- Continue button appears at 76s (5s after final paragraph)
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
