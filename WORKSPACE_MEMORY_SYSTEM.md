# Workspace Memory System

## Layers
1. `AGENTS.md` — durable operating rules
2. `MEMORY.md` — tiny routing/index layer
3. `memory/YYYY-MM-DD.md` — daily residue
4. `para/` — workspace-scoped durable truth
5. QMD — optional additive retrieval layer

## Guardrails
- Files are canonical truth.
- QMD does not replace files.
- Bootstrap files stay small.
- Durable memory stays inside the workspace by default.
