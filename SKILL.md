---
name: mermaid-illustrate
description: A comprehensive skill for creating all types of Mermaid diagrams including flowcharts, sequence diagrams, class diagrams, state diagrams, entity relationship diagrams, user journey diagrams, Gantt charts, pie charts, quadrant charts, requirement diagrams, Git graphs, C4 diagrams, mindmaps, timelines, ZenUML, Sankey diagrams, XY charts, block diagrams, packet diagrams, Kanban boards, architecture diagrams, radar charts, and treemaps. Use this skill whenever the user requests to create, draw, or visualize any diagram, flowchart, or structured chart using Mermaid syntax.
version: 1.0.0
author: zhiweio
license: MIT
tags:
  - mermaid
  - diagram
  - visualization
  - flowchart
  - architecture
  - blueprint
  - ibm-carbon
---

## When to use this skill

Use this skill whenever the user wants to:
- Create any type of diagram or flowchart
- Visualize processes, workflows, or system architectures
- Draw sequence diagrams, class diagrams, or state diagrams
- Create project timelines (Gantt charts)
- Visualize data relationships (ER diagrams, entity relationships)
- Create user journey maps
- Generate pie charts, quadrant charts, or other data visualizations
- Draw Git branching structures
- Create mindmaps or hierarchical structures
- Visualize system architectures (C4 diagrams)
- Create timelines or event sequences
- Generate any other diagram type supported by Mermaid

## Design Methodology: Blueprint (IBM Carbon · C4)

All diagrams follow the **Blueprint** design system — IBM Carbon v11 color tokens combined with C4 model layered thinking. Restrained, semantic, dark-mode ready.

### Core Principles

1. **Semantic Coloring** — Blue = processing, Teal = data, Amber = decision, Green = success, Red = error, Grey = external. Color carries meaning before labels are read.
2. **Restrained Palette** — Default to 4–6 colors; add more only when semantic complexity demands it.
3. **Hierarchy First** — Border weight, color intensity, and grouping guide the reader's eye along the primary path.
4. **Dark-Mode Ready** — Use `themeVariables` or `classDef` styling that renders on both light and dark backgrounds.
5. **No Emoji** — Emoji is **strictly prohibited** in all diagram text (labels, edges, titles, subgraphs). Use icons from `icon-catalog.md` or semantic coloring instead.
6. **Icon First** — Prefer icons from `icon-catalog.md` (logos/devicon/gcp/vscode-icons/codicon/skill-icons). Use icon-pack syntax (`@{ icon: }` / `(pack:icon)`) when registered; otherwise remote-URL `@{ img: }`. Never use emoji as an icon substitute.

### Standard Palette (IBM Carbon v11)

| Role | Fill | Stroke | classDef | When to Use |
|------|------|--------|----------|-------------|
| Process — System/Service | `#edf5ff` | `#0f62fe` | `bpProcess` | Microservices, handlers, processing |
| Data — Storage/Database | `#d9fbfb` | `#007d79` | `bpData` | Databases, caches, queues |
| Decision — Branch/Condition | `#fcf4d6` | `#f1c21b` | `bpDecision` | Conditionals, branching |
| Success — Complete/OK | `#defbe6` | `#198038` | `bpSuccess` | Terminal success, healthy |
| Error — Failure/Exception | `#fff1f1` | `#da1e28` | `bpError` | Error states, failure paths |
| External — Third-party | `#f2f4f8` | `#dde1e6` | `bpExternal` | External systems, third-party APIs |
| User — Person/Actor | `#f2f4f8` | `#697077` | `bpUser` | Human actors, personas |
| Info — Highlight/Meta | `#f6f2ff` | `#8a3ffc` | `bpInfo` | Annotations, key nodes |
| Group — Container/Boundary | `#f2f4f8` | `#dde1e6` | `bpGroup` | Subgraphs, boxes, groups |
| Boundary — Enterprise/Domain | `#ffffff` | `#393939` | `bpBoundary` | Enterprise/system boundaries |

Neutrals: text `#161616`, secondary text `#525252`, border `#dde1e6`, line `#697077`, canvas `#ffffff`.

### Reusable classDef Templates

```
classDef bpProcess  fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
classDef bpData     fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616
classDef bpSuccess  fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
classDef bpError    fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616
classDef bpExternal fill:#f2f4f8,stroke:#dde1e6,stroke-width:2px,color:#525252
classDef bpUser     fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
classDef bpInfo     fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px,color:#161616
classDef bpGroup    fill:#f2f4f8,stroke:#dde1e6,stroke-width:1px,color:#393939
classDef bpBoundary fill:#ffffff,stroke:#393939,stroke-width:2px,color:#393939
```

### Global Theme Variables (light)

For diagrams that support `themeVariables` (Flowchart, Sequence, State, ER, Class, Requirement, Timeline, Journey, Gantt):

```
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#edf5ff','primaryTextColor':'#161616','primaryBorderColor':'#0f62fe','lineColor':'#697077','secondaryColor':'#d9fbfb','tertiaryColor':'#f2f4f8'}}}%%
```

### Mindmap Theme Variables

Mindmaps use their own set of `themeVariables` (requires `'theme': 'base'`):

**Standard (light canvas)**:
```
%%{init: {'theme':'base','themeVariables':{'mindmapRootColor':'#0f62fe','mindmapTextColor':'#ffffff','mindmapMainColor':'#1d3649','mindmapSecondaryColor':'#393939','mindmapLineColor':'#697077'}}}%%
```

**Dark mode**:
```
%%{init: {'theme':'base','themeVariables':{'mindmapRootColor':'#4589ff','mindmapTextColor':'#f4f4f4','mindmapMainColor':'#0f62fe','mindmapSecondaryColor':'#525252','mindmapLineColor':'#878d96'}}}%%
```

> Mindmap supports only mindmap-specific variables (`mindmapRootColor`, `mindmapTextColor`, `mindmapMainColor`, `mindmapSecondaryColor`, `mindmapLineColor`). General `themeVariables` (e.g., `primaryColor`) have no effect on mindmaps. See `examples/mindmap.md` for full documentation.

> **Full spec**: `examples/design-system.md` — dark theme, line-style conventions, linkStyle patterns, and the complete IBM Carbon token mapping. Always load it first.

---

## How to use this skill

To create a Mermaid diagram:

1. **Identify the diagram type** from the user's request:
   - Flowchart/flow chart/流程图 → `flowchart` or `graph`
   - Sequence diagram/时序图 → `sequenceDiagram`
   - Class diagram/类图 → `classDiagram`
   - State diagram/状态图 → `stateDiagram` or `stateDiagram-v2`
   - Entity relationship diagram/实体关系图 → `erDiagram`
   - User journey/用户旅程图 → `journey`
   - Gantt chart/甘特图 → `gantt`
   - Pie chart/饼图 → `pie`
   - Quadrant chart/象限图 → `quadrantChart`
   - Requirement diagram/需求图 → `requirementDiagram`
   - Git graph/Git图 → `gitGraph`
   - C4 diagram/C4图 → `C4Context` or other C4 types
   - Mindmap/思维导图 → `mindmap`
   - Timeline/时间线图 → `timeline`
   - ZenUML/禅UML → `zenuml`
   - Sankey diagram/桑基图 → `sankey`
   - XY chart/XY图 → `xychart`
   - Block diagram/方块图 → `block`
   - Packet diagram/数据包图 → `packet`
   - Kanban/看板图 → `kanban`
   - Architecture diagram/架构图 → `architecture-beta`
   - Radar chart/雷达图 → `radar-beta`
   - Treemap/树状图 → `treemap-beta`

2. **Load the design system reference** first:
   - `examples/design-system.md` — Blueprint color palette, classDef templates, and common patterns (ALWAYS load this first)
   - `examples/icon-catalog.md` — Icon reference: 600+ icons across 13 technology categories covering logos, devicon, gcp, vscode-icons, codicon, and skill-icons icon sets (load when the diagram needs icons)

3. **Load the appropriate diagram example file** from `examples/`:
   - `examples/flowchart.md` — Flowcharts, process diagrams, and microservice architectures
   - `examples/sequence.md` — Sequence diagrams for interactions and API flows
   - `examples/class.md` — Class diagrams and object-oriented designs
   - `examples/state.md` — State diagrams and state machines
   - `examples/er.md` — Entity relationship diagrams and database schemas
   - `examples/journey.md` — User journey maps and experience flows
   - `examples/gantt.md` — Gantt charts and project timelines
   - `examples/pie.md` — Pie charts for proportions
   - `examples/quadrant.md` — Quadrant charts for prioritization matrices
   - `examples/requirement.md` — Requirement diagrams (SysML-style)
   - `examples/gitgraph.md` — Git branching and commit history diagrams
   - `examples/c4.md` — C4 architecture diagrams (Context, Container, Component, Deployment)
   - `examples/mindmap.md` — Mindmaps for hierarchical concept organization
   - `examples/timeline.md` — Timeline diagrams for chronological events
   - `examples/zenuml.md` — ZenUML sequence diagrams (concise syntax)
   - `examples/sankey.md` — Sankey diagrams for flow and magnitude visualization
   - `examples/xychart.md` — XY charts (bar, line, multiple series)
   - `examples/block.md` — Block diagrams with grid layout control
   - `examples/packet.md` — Packet diagrams for network protocol structures
   - `examples/kanban.md` — Kanban boards for workflow visualization
   - `examples/architecture.md` — Architecture diagrams for cloud/CI-CD deployments (3 approaches: bare, icon pack, flowchart img)
   - `examples/radar.md` — Radar/spider charts for multi-dimensional comparison
   - `examples/treemap.md` — Treemap diagrams for hierarchical proportion visualization

4. **Follow the syntax and Blueprint styling instructions** in the example file

5. **Generate the Mermaid code** wrapped in a Markdown code block with proper syntax highlighting:
   
   **IMPORTANT**: Always wrap the Mermaid code in a Markdown code block with `mermaid` language tag. This ensures the format is preserved when users copy the content.
   
   **Example format** (use actual Mermaid syntax, not placeholders):
   ```mermaid
   flowchart TD
       A[Start] --> B[Process]
       B --> C[End]
   ```
   
   **Output Format Requirements**:
   - Always use triple backticks (```) with `mermaid` language tag
   - Never output raw Mermaid code without code block markers
   - The code block must be complete and properly formatted
   - Use actual valid Mermaid syntax, not placeholders like `<diagram-type>` or `...diagram content...`
   - This ensures users can copy the code without losing formatting

6. **Include Blueprint styling** (only for diagrams that support styling directives):

   **Styling support by diagram type** — only apply directives where supported:
   
   | Diagram | `classDef`+`class`/`cssClass` | `style` | `linkStyle` | `themeVariables` |
   |---------|:---:|:---:|:---:|:---:|
   | `flowchart` / `graph` | ✅ | ✅ | ✅ | ✅ |
   | `stateDiagram` / `stateDiagram-v2` | ✅ | ✅ | ❌ | ✅ |
   | `classDiagram` | ✅ (`cssClass`) | ✅ | ❌ | ✅ |
   | `erDiagram` | ✅ | ✅ | ❌ | ✅ |
   | `requirementDiagram` | ✅ | ✅ | ❌ | ✅ |
   | `quadrantChart` | ✅ | ✅ (per-point) | ❌ | ❌ |
   | `treemap-beta` | ✅ (`:::` shorthand) | ❌ | ❌ | ❌ |
   | `block-beta` | ✅ | ✅ | ❌ | ✅ |
   | `sequenceDiagram` | ❌ (use `box` color) | ❌ (use `box`/`rect`) | ❌ | ✅ |
   | `gantt` | ❌ (use `done`/`active`/`crit`/`milestone` tags) | ❌ | ❌ | ✅ (via frontmatter `themeCSS`) |
   | `pie` | ❌ | ❌ | ❌ | ✅ |
   | `journey` | ❌ | ❌ | ❌ | ✅ |
   | `gitGraph` | ❌ | ❌ | ❌ | ✅ |
   | `timeline` | ❌ | ❌ | ❌ | ✅ |
   | `mindmap` | ❌ (use `:::` shorthand inline) | ❌ | ❌ | ✅ (mindmap-specific vars only) |
   | `C4Context` / C4 types | ❌ (use `UpdateElementStyle`/`UpdateRelStyle`) | ❌ | ❌ | ❌ |
   | `architecture-beta` | ❌ | ❌ | ❌ | ❌ |
   | `sankey` | ❌ | ❌ | ❌ | ❌ |
   | `xychart` | ❌ | ❌ | ❌ | ❌ |
   | `kanban` | ❌ | ❌ | ❌ | ❌ |
   | `packet` | ❌ | ❌ | ❌ | ❌ |
   | `radar-beta` | ❌ | ❌ | ❌ | ❌ |
   | `zenuml` | ❌ | ❌ | ❌ | ❌ |
   
   > **Key rules**:
   > - **`linkStyle`** — **flowchart/graph ONLY**. Sequence diagrams, class diagrams, state diagrams, Gantt charts, etc. do NOT support `linkStyle`; remove `linkStyle` from those diagram types.
   > - **`classDef` + `class`** — supported in: flowchart, stateDiagram, classDiagram (uses `cssClass`), erDiagram, requirementDiagram, block-beta, treemap-beta (`:::`), quadrantChart (per-point radii MUST be ≤6 per `examples/quadrant.md`). Remove `classDef`/`class` from all other diagram types.
   > - **`themeVariables`** — supported in: flowchart, sequence, state, ER, class, requirement, timeline, journey, Gantt, pie, gitGraph, block, mindmap (mindmap uses its own mindmap-specific variables: `mindmapRootColor`, `mindmapTextColor`, `mindmapMainColor`, `mindmapSecondaryColor`, `mindmapLineColor`; general variables like `primaryColor` have no effect). For unsupported types, remove the `%%{init: ...}%%` directive.
   > - **C4** uses its own styling: `UpdateElementStyle()` / `UpdateRelStyle()` — does NOT support `classDef`/`linkStyle`/`themeVariables`.
   > - For diagrams without styling support, convey semantics through naming, structure, or built-in tags (e.g., Gantt's `done`/`active`/`crit`/`milestone`).
   
   When styling IS supported:
   - Use the Blueprint palette — never use ad-hoc colors
   - Use semantic class names: `bpProcess`, `bpData`, `bpDecision`, `bpSuccess`, `bpError`, `bpExternal`, `bpUser`, `bpInfo`
   - In flowcharts: apply `linkStyle` for flow emphasis (primary flows: thicker, blue; data flows: teal with dashes)

7. **Icons and Images — Syntax Selection by Registration State**:
   - **Icon Selection**: Load `examples/icon-catalog.md` first to find the right icon. Contains 600+ pre-listed icons across 6 icon sets (logos, devicon, gcp, codicon, skill-icons, vscode-icons) organized in 13 technology categories. Icon lookup priority: `logos` (cloud/product logos) → `devicon` (languages/tools/frameworks) → `gcp` (Google Cloud services, 214 icons) → `vscode-icons` (file-type icons, 1,513 icons) → `codicon` (IDE/dev concepts) → `skill-icons` (needs theme variants).
   - **Decision rule — pick ONE syntax per diagram, do not mix**:
     - **Icon packs registered** (detected/known) → use **icon-pack syntax**:
       - Flowchart: `@{ icon: "pack:icon-name", form: "square", label: "Label", pos: "t", h: 60 }` — only set `h` (minimum 48)
       - architecture-beta: `service id(pack:icon-name)[Label]`, `group id(pack:icon-name)[Label]` — e.g. `service ec2(logos:aws-ec2)[EC2]`
       - FontAwesome: `A[fa:fa-user User]` — requires separately registering the optional `fa` pack
     - **Icon packs NOT registered** → use the **remote-URL fallback** (works everywhere, no setup):
       - `@{ img: "https://api.iconify.design/{prefix}/{icon-name}.svg", label: "Label", pos: "b", h: 48, constraint: "on" }`
   - **`@{ img: }` aspect-ratio rule**: NEVER set both `w` and `h` simultaneously — it forces stretching and distorts non-square icons. Only set `h`, enable `constraint: "on"` to auto-calculate width preserving aspect ratio. SVG URL pattern: `https://api.iconify.design/{prefix}/{icon}.svg`
   - **Canonical registration snippet** (6 packs: logos, skill-icons, devicon, codicon, gcp, vscode-icons). Use when the environment supports `registerIconPacks()` (self-hosted/bundler/mkdocs); NOT needed for mermaid.live or GitHub:
     ```javascript
     (function () {
       function registerIcons() {
         if (typeof mermaid === 'undefined') { setTimeout(registerIcons, 100); return; }
         var iconPacks = ['logos', 'skill-icons', 'devicon', 'codicon', 'gcp', 'vscode-icons'];
         try {
           mermaid.registerIconPacks(iconPacks.map(function (name) {
             return { name: name, loader: function () {
               return fetch('https://unpkg.com/@iconify-json/' + name + '/icons.json').then(function (res) { return res.json(); });
             }};
           }));
         } catch (e) { console.warn('Icon pack registration failed:', e.message); }
       }
       registerIcons();
     })();
     ```
   - Reference: `examples/design-system.md` for complete icon usage guide with aspect ratio warnings. `examples/icon-catalog.md` for the comprehensive icon reference. `examples/architecture.md` for the 3-approach model (bare / icon pack / remote URL).

8. **Validate the syntax**:
   - Ensure all required elements are present
   - Check that relationships and connections are properly defined
   - Verify date formats for Gantt charts
   - Confirm data formats for charts (pie, quadrant, etc.)

9. **Save the diagram to project directory**:
   - **Default behavior**: When generating a Mermaid diagram, save it to the current project directory
   - **Recommended locations**:
     - `docs/diagrams/` - For documentation diagrams
     - `docs/` - For general documentation
     - `diagrams/` - For standalone diagram files
     - Current directory (`.`) - If no specific directory structure exists
   - **File naming**: Use descriptive names like `system-architecture.md`, `user-flow.md`, `database-schema.md`, etc.
   - **File format**: Save as `.md` file with the Mermaid code block inside
   - **Example**: If user requests a system architecture diagram, save it as `docs/diagrams/system-architecture.md` or `diagrams/system-architecture.md`
   - **Ask if needed**: If the project structure is unclear, ask the user where they'd like the diagram saved, but default to creating a `docs/` or `diagrams/` directory if it doesn't exist

**Output Format and File Saving**:

When generating a diagram, follow this response structure:

1. **Save the file first**: Create the diagram file in the project directory (e.g., `docs/diagrams/system-architecture.md`)

2. **Inform the user**: Tell them where the file was saved

3. **Display the diagram**: Show the Mermaid code in a properly formatted Markdown code block with `mermaid` language tag

**Example Response Structure**:
- First line: "I've created the Mermaid diagram and saved it to `docs/diagrams/system-architecture.md`."
- Then show the diagram wrapped in a code block:
  - Start with: three backticks + `mermaid` + newline
  - Then the Mermaid code
  - End with: three backticks + newline

**Critical Requirements**:
- The Mermaid code block MUST ALWAYS be properly formatted with triple backticks (```) and `mermaid` language tag
- NEVER output raw Mermaid code without code block markers
- The code block must be complete (opening and closing backticks)
- This ensures users can copy the code without losing formatting
- Always save the diagram file to the current project directory (default: `docs/diagrams/` or `diagrams/`)

If the diagram type doesn't match any existing example, refer to the Mermaid documentation or ask the user for clarification about the desired visualization.

## Keywords

mermaid, diagram, flowchart, flow chart, sequence diagram, class diagram, state diagram, entity relationship, ER diagram, user journey, Gantt chart, pie chart, quadrant chart, requirement diagram, Git graph, C4 diagram, mindmap, timeline, ZenUML, Sankey diagram, XY chart, block diagram, packet diagram, Kanban, architecture diagram, radar chart, treemap, icon pack, iconify, devicon, codicon, aws icons, cloud architecture, 流程图, 时序图, 类图, 状态图, 实体关系图, 用户旅程图, 甘特图, 饼图, 象限图, 需求图, Git图, C4图, 思维导图, 时间线图, 桑基图, XY图, 方块图, 数据包图

