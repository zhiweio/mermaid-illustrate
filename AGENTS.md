# AGENTS.md

Instructions for AI coding agents working on this repository.

---

## Project Overview

This is an **AI Agent Skill** for creating Mermaid diagrams. It follows the [Agent Skills specification](https://agentskills.io) — a `SKILL.md` file with YAML frontmatter that agents discover and load on demand. The skill provides guidance for generating 23 types of Mermaid diagrams with a unified IBM Carbon Blueprint design system.

- **Skill name**: `mermaid-illustrate`
- **Entry point**: `SKILL.md`
- **Reference material**: `examples/` (25 files, loaded on demand by agents)
- **Design system**: Blueprint (IBM Carbon v11 + C4 model)

---

## Repository Conventions

### File Organization

- `SKILL.md` — Main skill definition. Keep under 500 lines. Contains the YAML frontmatter that agents scan for discovery and the core workflow instructions.
- `examples/` — Reference files. Each covers one diagram type. Follow the format: `## Instructions` → `### Blueprint Styling` → `### Syntax` → `### Example(s)` → `### Alternative (if applicable)`.
- `README.md` — Human-facing documentation. Do NOT duplicate SKILL.md content here; keep it focused on installation, usage, and project overview.
- `AGENTS.md` — This file. Workspace-level instructions for agents working on this repo.

### Design System Consistency

All diagram examples MUST use the Blueprint design system:
- IBM Carbon v11 color tokens (defined in `examples/design-system.md`)
- Semantic classDef names: `bpProcess`, `bpData`, `bpDecision`, `bpWarning`, `bpSuccess`, `bpError`, `bpExternal`, `bpUser`, `bpInfo`, `bpGroup`, `bpBoundary`
- **classDef in code blocks must match canonical definitions exactly**: every `classDef` must include `color:#161616` (or `color:#525252` for `bpExternal`, `color:#393939` for `bpGroup`/`bpBoundary`). Do not omit the `color` attribute.
- **`bpExternal` text color is `#525252`** (not `#697077`). This is a common mistake.
- No ad-hoc colors — always reference the palette
- No emoji in diagram text, labels, edges, titles, or subgraphs

### When Adding or Modifying Examples

1. Load `examples/design-system.md` first for the canonical palette
2. Follow the existing example structure (Instructions → Blueprint Styling → Syntax → Examples)
3. Include at least one complete working example with Blueprint styling applied
4. Update `SKILL.md` if the styling support matrix needs changes (new diagram support, deprecated features)
5. Keep files focused — one diagram type per file

### Writing Style

- Write instructions in **third-person imperative** ("Use the `mindmap` keyword", "Apply Blueprint styling")
- Include **negative constraints** where appropriate ("Do NOT use ad-hoc colors", "`linkStyle` only works in flowcharts")
- Prefer **declarative bullet lists** for conventions; use **numbered steps** only for ordered workflows
- Store information once — do not duplicate content between `SKILL.md` and `examples/`

### Frontmatter Conventions

The `SKILL.md` frontmatter follows the Agent Skills specification:
- `name`: Must match the installed directory name (`mermaid`)
- `description`: Drives agent triggering — include trigger keywords and diagram type names
- `tags`: Lowercase, hyphenated, relevant to discovery

---

## Testing / Validation

When modifying examples, verify:

- [ ] Mermaid syntax is valid (test on [mermaid.live](https://mermaid.live) or with `mermaid-cli`)
- [ ] Blueprint styling is applied correctly (classDef matches design-system.md)
- [ ] No emoji appear in diagram code
- [ ] The example file follows the standard structure
- [ ] Links to other reference files are correct (relative paths within `examples/`)

---

## Key Constraints

1. **No emoji** — Strictly prohibited in all diagram content
2. **Blueprint palette only** — Never introduce ad-hoc hex colors
3. **Keep SKILL.md lean** — Push detailed reference material to `examples/`
4. **No duplicate content** — Each piece of information lives in exactly one place; `classDef` templates are canonical in `design-system.md`, not duplicated in other files
5. **Progressive disclosure** — `examples/` files are loaded on demand, not pre-loaded
6. **`linkStyle` is flowchart/graph ONLY** — Remove from all other diagram types
7. **classDef `color` attribute is mandatory** — Every `classDef` declaration must include the correct `color` attribute matching `design-system.md`
8. **`bpExternal` color is `#525252`** — Not `#697077`; this is a frequently-inherited mistake from older code blocks
9. **No non-canonical classDef names** — Do not invent names like `bpStart`/`bpEnd`; use `bpProcess`/`bpSuccess` instead

---

## Useful References

- [Agent Skills Specification](https://agentskills.io)
- [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- [Mermaid Documentation](https://mermaid.js.org/)
- [IBM Carbon Design System](https://carbondesignsystem.com/)
