# Agent Instructions

Load context from `.kilocode/rules/memory-bank/` before starting work.

## Load Order

1. `brief.md` — What is this project?
2. `product.md` — Why does it exist?
3. `context.md` — Where are we now? (most frequently updated)
4. `architecture.md` — How is it structured?
5. `tech.md` — What technologies and constraints?
6. `tasks.md` — Repetitive workflows (if present)

## Key Files

| File | Update Frequency |
|------|------------------|
| `context.md` | Every session |
| `architecture.md` | When structure changes |
| `tech.md` | When stack changes |
| `product.md` | When goals evolve |
| `brief.md` | Rarely |

## Session Pattern

1. Load memory bank files in order above
2. Confirm context loaded
3. Do work
4. Update `context.md` before session ends
5. Update other memory bank files if relevant changes occurred
