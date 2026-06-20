# Mermaid Illustrate

> **AI Agent Skill** — Professional Mermaid diagrams with the IBM Carbon Blueprint design system.

A comprehensive, production-grade skill for AI coding agents (Claude Code, ZCode, GitHub Copilot, Cursor, and more) to create 23 types of Mermaid diagrams with a unified, semantic, dark-mode-ready visual language based on IBM Carbon Design System v11.

---

## What This Skill Does

- Creates **23 types** of Mermaid diagrams: flowcharts, sequence diagrams, class diagrams, state machines, ER diagrams, user journeys, Gantt charts, pie charts, quadrant charts, requirement diagrams, Git graphs, C4 architecture diagrams, mindmaps, timelines, ZenUML, Sankey diagrams, XY charts, block diagrams, packet diagrams, Kanban boards, architecture diagrams, radar charts, and treemaps.
- Applies the **Blueprint design system** — semantic IBM Carbon v11 colors that carry meaning before labels are read.
- Supports **600+ icons** across 6 icon sets (logos, devicon, gcp, vscode-icons, codicon, skill-icons) with smart syntax selection.
- Handles **dark-mode** and **light-mode** automatically.
- Follows **progressive disclosure** — agents only load what's needed, keeping context windows lean.

---

## Design System: Blueprint

Built on **IBM Carbon v11** color tokens + **C4 model** layered thinking:

| Principle | Description |
|-----------|-------------|
| **Semantic Coloring** | Blue = processing, Teal = data, Amber = decision, Green = success, Red = error, Grey = external |
| **Restrained Palette** | 4–6 colors by default; add more only when semantic complexity demands it |
| **Hierarchy First** | Border weight and color intensity guide the reader's eye |
| **Dark-Mode Ready** | `themeVariables` and `classDef` styling renders on both light and dark backgrounds |
| **No Emoji** | Emoji strictly prohibited — use icons or semantic coloring instead |
| **Icon First** | Prefer icons from the 600+ icon catalog over text labels |

See [`examples/design-system.md`](examples/design-system.md) for the full specification.

---

## Supported Diagram Types

| Category | Diagram Types |
|----------|--------------|
| **Flow & Process** | Flowchart, Sequence, State, ZenUML |
| **Structure & Data** | Class, ER, Block, Packet, Treemap |
| **Architecture** | C4 (Context/Container/Component/Deployment), Architecture (beta) |
| **Project & Time** | Gantt, Timeline, Git Graph, Kanban |
| **User & Experience** | User Journey, Mindmap |
| **Charts & DataViz** | Pie, Quadrant, XY Chart, Radar, Sankey |
| **Requirements** | Requirement (SysML-style) |

---

## Installation

### Quick Install (ZCode / Claude Code)

```bash
# Clone directly into the skills directory
git clone https://github.com/zhiweio/mermaid-illustrate.git ~/.agents/skills/mermaid-illustrate
```

Or install per-project:

```bash
git clone https://github.com/zhiweio/mermaid-illustrate.git /path/to/your-project/.agents/skills/mermaid-illustrate
```

### Per-Agent Install Paths

| Agent | Global Path | Project Path |
|-------|------------|--------------|
| **Claude Code / ZCode** | `~/.agents/skills/mermaid-illustrate/` | `.agents/skills/mermaid-illustrate/` |
| **GitHub Copilot** | `~/.copilot/skills/mermaid-illustrate/` | `.github/skills/mermaid-illustrate/` |
| **Cursor** | `~/.cursor/skills/mermaid-illustrate/` | `.cursor/skills/mermaid-illustrate/` |
| **Codex CLI** | `~/.codex/skills/mermaid-illustrate/` | `.codex/skills/mermaid-illustrate/` |
| **Gemini CLI** | `~/.gemini/skills/mermaid-illustrate/` | `.gemini/skills/mermaid-illustrate/` |
| **Windsurf** | `~/.codeium/windsurf/skills/mermaid-illustrate/` | `.windsurf/skills/mermaid-illustrate/` |

### Using CLI Installers

```bash
# Vercel Skills CLI
npx skills add zhiweio/mermaid-illustrate

# vskill
npx vskill install zhiweio/mermaid-illustrate

# Skilz (Python)
pip install skilz
skilz install zhiweio/mermaid-illustrate
```

---

## Usage

### Triggering the Skill

Simply describe what you want to your agent. The skill activates automatically when you mention diagram-related terms:

**English triggers:**
- "Create a flowchart of the user login process"
- "Draw a sequence diagram showing the API authentication flow"
- "Make a C4 container diagram for our microservices architecture"
- "Generate a mindmap of the project structure"
- "Create a Gantt chart for the Q3 release plan"

**Chinese triggers:**
- "画一个用户登录的流程图"
- "创建一个微服务架构的时序图"
- "做一个数据库 ER 图"
- "生成项目甘特图"
- "绘制思维导图"

### What the Agent Does

1. Identifies the diagram type from your request
2. Loads the Blueprint design system and the relevant example file
3. Generates Mermaid code with IBM Carbon styling
4. Saves the diagram to `docs/diagrams/` in your project
5. Displays the rendered diagram

### Example Output

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#edf5ff','primaryTextColor':'#161616','primaryBorderColor':'#0f62fe','lineColor':'#697077','secondaryColor':'#d9fbfb','tertiaryColor':'#f2f4f8'}}}%%
flowchart TD
    Start([Start]) --> Process[Process Data]
    Process --> Decision{Valid?}
    Decision -->|Yes| Success[Save]
    Decision -->|No| Error[Error]
    Success --> End([End])
    Error --> End

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616

    class Process bpProcess
    class Decision bpDecision
    class Success bpSuccess
    class Error bpError
```

---

## Supported Agents / Platforms

| Agent | Status | Notes |
|-------|--------|-------|
| **Claude Code** | ✅ Full support | Native SKILL.md + frontmatter |
| **ZCode** | ✅ Full support | Native SKILL.md + frontmatter |
| **GitHub Copilot** | ✅ Supported | `.github/skills/` path |
| **Cursor** | ✅ Supported | `.cursor/skills/` or `.cursor/rules/` |
| **Codex CLI (OpenAI)** | ✅ Supported | Native skills support |
| **Gemini CLI** | ✅ Supported | `.gemini/skills/` path |
| **Windsurf** | ✅ Supported | `.codeium/windsurf/skills/` path |
| **JetBrains AI** | ✅ Supported | Skills directory |

---

## Project Structure

```
mermaid-illustrate/
├── SKILL.md                    # Main skill definition (frontmatter + instructions)
├── README.md                   # This file — human-facing documentation
├── AGENTS.md                   # Workspace instructions for agents contributing to this repo
├── LICENSE                     # MIT License
├── .gitignore
└── examples/                   # 25 reference files (loaded on demand, not pre-loaded)
    ├── design-system.md        # Blueprint palette, classDef templates, theme configs
    ├── icon-catalog.md         # 600+ icons across 13 categories, 6 icon sets
    ├── flowchart.md            # Flowcharts, process diagrams, microservice architectures
    ├── sequence.md             # Sequence diagrams for API flows and interactions
    ├── class.md                # Class diagrams and OO designs
    ├── state.md                # State machines and state diagrams
    ├── er.md                   # Entity relationship diagrams and DB schemas
    ├── journey.md              # User journey maps
    ├── gantt.md                # Gantt charts and project timelines
    ├── pie.md                  # Pie charts
    ├── quadrant.md             # Quadrant charts
    ├── requirement.md          # SysML-style requirement diagrams
    ├── gitgraph.md             # Git branching and commit history
    ├── c4.md                   # C4 architecture (Context, Container, Component, Deployment)
    ├── mindmap.md              # Mindmaps with Blueprint IBM Carbon theming
    ├── timeline.md             # Chronological event timelines
    ├── zenuml.md               # ZenUML sequence diagrams
    ├── sankey.md               # Sankey flow diagrams
    ├── xychart.md              # XY charts (bar, line, multi-series)
    ├── block.md                # Block diagrams with grid layout
    ├── packet.md               # Network protocol packet diagrams
    ├── kanban.md               # Kanban workflow boards
    ├── architecture.md         # Cloud/CI-CD architecture (3 approaches)
    ├── radar.md                # Radar/spider charts
    └── treemap.md              # Hierarchical treemap diagrams
```

### Progressive Disclosure (How Agents Load This)

| Level | What | Token Cost | When |
|-------|------|------------|------|
| **L1** | `name` + `description` from frontmatter | ~50 tokens | Always in context |
| **L2** | Full `SKILL.md` body (~290 lines) | ~3,500 tokens | On trigger (diagram request) |
| **L3** | `examples/*.md` reference files | ~1,000–2,000 each | Only when specific diagram type is needed |

---

## Contributing

Contributions are welcome! Areas where help is especially valuable:

- **New diagram examples** — Add more real-world usage patterns to `examples/`
- **Icon additions** — Expand the `examples/icon-catalog.md` with missing technologies
- **Testing** — Test the skill with different agent platforms and report issues
- **Documentation** — Improve clarity, add screenshots of rendered diagrams

### Guidelines

1. Follow the Blueprint design system (IBM Carbon v11 colors) consistently
2. Keep SKILL.md under 500 lines — push deep content to `examples/`
3. Match the existing code style and comment density
4. No emoji in any diagram content or labels

---

## License

MIT © [zhiweio](https://github.com/zhiweio)

---

## Related

- [Mermaid Documentation](https://mermaid.js.org/) — Official Mermaid syntax reference
- [IBM Carbon Design System](https://carbondesignsystem.com/) — Color tokens and design philosophy
- [C4 Model](https://c4model.com/) — Architecture visualization framework
- [Agent Skills Specification](https://agentskills.io) — Open standard for AI agent skills
- [Anthropic Agent Skills Guide](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
