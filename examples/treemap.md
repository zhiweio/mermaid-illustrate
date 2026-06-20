## Instructions

Treemap diagrams display hierarchical data as a set of nested rectangles. Each branch of the tree is represented by a rectangle, which is then tiled with smaller rectangles representing sub-branches. The size of each rectangle is proportional to the value it represents.

### Blueprint Styling

Treemap supports `:::className` syntax with `classDef`. Apply Blueprint colors to distinguish categories (Product, Region, etc.).

### Syntax

- Use `treemap-beta` keyword (requires Mermaid v11.0.0+, experimental feature 🔥)
- Section/Parent nodes: `"Section Name"` (quoted text)
- Leaf nodes with values: `"Leaf Name": value` (quoted text followed by colon and value)
- Hierarchy: Created using indentation (spaces or tabs)
- Styling: Nodes can be styled using `:::class` syntax
- Root node: The first node is the root of the tree
- **Important**: If your environment doesn't support treemap, use the flowchart alternative below

Reference: [Mermaid Treemap Diagram Documentation](https://mermaid.ai/open-source/syntax/treemap.html)

### Example (Basic Treemap)

```mermaid
treemap-beta
"Sales"
    "Region A": 500
    "Region B": 300
    "Region C": 200
```

### Example (Hierarchical Treemap)

```mermaid
treemap-beta
"Sales"
    "Region A": 500
        "Product A1": 200
        "Product A2": 150
        "Product A3": 150
    "Region B": 300
        "Product B1": 120
        "Product B2": 180
    "Region C": 200
        "Product C1": 100
        "Product C2": 100
```

### Example (With Styling)

```mermaid
treemap-beta
"Sales":::primary
    "Region A": 500:::regionA
    "Region B": 300:::regionB
    "Region C": 200:::regionC

classDef primary fill:#0f62fe,stroke:#0f62fe,stroke-width:2px,color:#fff
classDef regionA fill:#d9fbfb,stroke:#007d79,stroke-width:1px,color:#161616
classDef regionB fill:#edf5ff,stroke:#0f62fe,stroke-width:1px,color:#161616
classDef regionC fill:#f6f2ff,stroke:#8a3ffc,stroke-width:1px,color:#161616
```

### Example (File System Structure)

```mermaid
treemap-beta
"Disk Usage":::primary
    "System": 500
        "Applications": 200
        "Library": 150
        "Users": 150
    "Documents": 300
        "Projects": 180
        "Downloads": 120
    "Media": 200
        "Photos": 120
        "Videos": 80

classDef primary fill:#393939,stroke:#161616,stroke-width:2px,color:#fff
```

### Example (Budget Allocation)

```mermaid
treemap-beta
"Budget":::root
    "Development": 50000
        "Salaries": 35000
        "Tools": 10000
        "Training": 5000
    "Marketing": 30000
        "Advertising": 20000
        "Events": 10000
    "Operations": 20000
        "Infrastructure": 15000
        "Support": 5000

classDef root fill:#393939,stroke:#161616,stroke-width:2px,color:#fff
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If treemap diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    Root["Sales: 1000"]
    A["Region A: 500"]
    B["Region B: 300"]
    C["Region C: 200"]

    Root --> A
    Root --> B
    Root --> C

    A1["Product A1: 200"]
    A2["Product A2: 150"]
    A3["Product A3: 150"]

    A --> A1
    A --> A2
    A --> A3

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class Root,A,B,C,A1,A2,A3 bpProcess
```
