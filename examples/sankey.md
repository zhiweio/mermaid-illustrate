## Instructions

Sankey diagrams visualize flow and relationships between entities, showing the magnitude of flows between nodes.

### Blueprint Styling

Sankey diagrams have limited styling support. Use the flowchart alternative for colored diagrams.

### Syntax

- Use `sankey` keyword (requires Mermaid v10.3.0+, experimental)
- Format: CSV style with exactly **3 columns**: `Source,Target,Value`
- Each line represents one flow: `source,target,value`
- **Empty lines are allowed** (for visual separation, without comma separators)
- Node names with **commas** must be wrapped in quotes: `"Node, Name"`
- Node names with **double quotes** use two quotes: `"He said ""Hello"""`
- Values should be numeric
- **Important**: Do NOT use arrow syntax (`-->|Value|`). Use CSV format instead.
- **Important**: If your environment doesn't support sankey, use the flowchart alternative below

Reference: [Mermaid Sankey Documentation](https://mermaid.ai/open-source/syntax/sankey.html)

### Example (Sankey - requires Mermaid v10.3.0+)

```mermaid
sankey
Energy Production,Electricity,100
Energy Production,Heat,30

Electricity,Residential,80
Electricity,Industrial,20

Heat,Residential,25
Heat,Industrial,5
```

### Example (User Flow — Acquisition Funnel)

```mermaid
sankey
Landing Page,Sign Up,500
Social Media,Landing Page,300
Email Campaign,Landing Page,200

Sign Up,Free Trial,350
Sign Up,Direct Purchase,100
Sign Up,Bounce,50

Free Trial,Purchase,150
Free Trial,Expired,200
```

### Example with Special Characters

```mermaid
sankey
Source A,Target B,50
"Source, with comma","Target with ""quotes""",30
Source C,Target D,20
```

### Alternative (Flowchart — Blueprint Style)

```mermaid
flowchart LR
    EP[Energy Production]
    E[Electricity]
    H[Heat]
    R[Residential]
    I[Industrial]

    EP -->|100| E
    EP -->|30| H
    E -->|80| R
    E -->|20| I
    H -->|25| R
    H -->|5| I

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616

    class EP bpProcess
    class E,H bpData
    class R,I bpProcess
```
