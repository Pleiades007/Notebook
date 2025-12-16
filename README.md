# Research Lab Notebook

State Ledger system for tracking research projects across sessions and AI systems (Claude + ChatGPT).

---

## Structure

```
Notebook/
  README.md                    ← You are here
  PROJECTS/
    project-name/
      STATE.md                 ← Single source of truth for project state
      DEFINITIONS.md           ← Locked definitions (prevent semantic drift)
      DECISIONS.md            ← Append-only decision log with audit trail
      NOTES.md                ← Scratchpad (not tracked in state)
      ARTIFACTS/              ← Outputs (figures, tables, data exports)
      STATE_HISTORY/          ← Historical snapshots
```

---

## Current Projects

### HIV Reservoir Research
- **Location:** `PROJECTS/hiv-reservoir/`
- **Status:** Initialized 2025-12-16
- **Description:** [Add project description]

---

## How to Use

### Starting a Session (Claude or ChatGPT)

```
"Load PROJECTS/hiv-reservoir and summarize state"
```

The AI will:
- Read STATE.md (current status)
- Read DEFINITIONS.md (locked terms)
- Read DECISIONS.md (decision history)
- Show you a 3-line summary

### Working

Work normally! The AI tracks state internally (`State: untracked` mode).

### Saving Progress

```
"update state"
```

The AI will:
- Generate updated STATE.md with new STATE_ID
- Append new decisions to DECISIONS.md
- Update DEFINITIONS.md if terms locked
- Show STATE DELTA (what changed)
- Tag which AI system made the updates

### Cross-System Continuity

**Session 1 (Claude):**
- Load → Work → Update state
- STATE.md says "LAST_UPDATED_BY: Claude Sonnet 4.5"

**Session 2 (ChatGPT):**
- Load → Sees Claude's work → Continue
- STATE.md says "LAST_UPDATED_BY: ChatGPT o1"
- PREVIOUS_STATE points to Claude's version

Full audit trail of who contributed what!

---

## Key Commands

```
"load state"                    → Start session
"update state"                  → Save to GitHub
"show state"                    → Display current state
"lock definition: [term]"       → Define a term
"check drift"                   → Verify consistency
```

---

## File Roles

**STATE.md** = "Here's where we are now"
- Current goal, assumptions, decisions, uncertainties, next steps
- Completely rewritten on each "update state"

**DECISIONS.md** = "Here's what we decided and why"
- Append-only (never deletes)
- Each decision tagged with AI, date, rationale, impact, reversibility
- Full audit trail

**DEFINITIONS.md** = "Here's what terms mean"
- Prevents confusion when switching between AI systems
- Only updated via explicit DEFINITION UPDATE

**NOTES.md** = "Random thoughts, not official yet"
- Scratchpad for exploration
- Not tracked in state

---

## Adding New Projects

1. Create folder: `PROJECTS/your-project-name/`
2. Copy the 4 core files from an existing project
3. Update STATE.md with your project details
4. Start working!

