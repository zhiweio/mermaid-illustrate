## Instructions

Quadrant charts display items in a 2x2 grid based on two criteria, useful for prioritization and analysis.

### Blueprint Styling

Quadrant charts support per-point `color`, `stroke-color`, `stroke-width`, and per-class styling. Use semantic colors: high-value = green, high-cost = red, medium = amber.

**Point Radius Rule**: All visible quadrant points MUST use a restrained radius of **4–6** (not larger than 6). The coordinate space is 0–1, so radii ≥ 10 produce disproportionately large circles that dominate the chart. Use `radius: 0` only for hidden-dot multi-line labels (see below). **Never** use `radius` values above 6 for data points.

### Syntax

- Use `quadrantChart` keyword
- Title: `title Chart Title` (optional)
- X-axis: `x-axis Left Label --> Right Label` or `x-axis Left Label` (only left)
- Y-axis: `y-axis Bottom Label --> Top Label` or `y-axis Bottom Label` (only bottom)
- Quadrants: `quadrant-1 Label`, `quadrant-2 Label`, `quadrant-3 Label`, `quadrant-4 Label`
  - `quadrant-1`: Top right quadrant
  - `quadrant-2`: Top left quadrant
  - `quadrant-3`: Bottom left quadrant
  - `quadrant-4`: Bottom right quadrant
- Points: `Point Name: [x, y]` where x and y values are in the range 0-1
- Point styling: `Point Name: [x, y] radius: 6, color: #da1e28, stroke-color: #0f62fe, stroke-width: 5px`
- Class styling: `Point Name:::className: [x, y]` with `classDef className color: #198038, radius: 6`
- **Multi-line data-point labels (hidden-dot overlay)**: `quadrantChart` natively does NOT support manual line breaks (`<br>`/`\n` are ignored in point labels). To split a point's text across multiple lines, stack additional points at the same X with the Y offset by a **fixed delta of `0.035`** and set their `radius: 0` (hides the dot) so only the text shows — visually faking a multi-line label.

```
"主标签 ": [x, y]
"副标签": [x, y - 0.035] radius: 0
```

> 固定高差使用 `0.035`（小于此值副标签会与主标签重叠；大于此值行距过宽）。主标签末尾留一个空格以与副标签对齐。

Reference: [Mermaid Quadrant Chart Documentation](https://mermaid.ai/open-source/syntax/quadrantChart.html)

### Example (Basic Quadrant Chart)

```mermaid
quadrantChart
    title Product Prioritization
    x-axis Low Effort --> High Effort
    y-axis Low Impact --> High Impact
    quadrant-1 Should Do
    quadrant-2 Must Do
    quadrant-3 Won't Do
    quadrant-4 Nice to Have
    Feature A: [0.3, 0.8]
    Feature B: [0.7, 0.9]
    Feature C: [0.2, 0.3]
    Feature D: [0.8, 0.2]
```

### Example (With Point Styling)

```mermaid
quadrantChart
    title Performance vs Cost
    x-axis Low Cost --> High Cost
    y-axis Low Performance --> High Performance
    quadrant-1 High Cost, High Performance
    quadrant-2 Low Cost, High Performance
    quadrant-3 Low Cost, Low Performance
    quadrant-4 High Cost, Low Performance
    Product A: [0.9, 0.0] radius: 6, color: #da1e28
    Product B: [0.8, 0.1] radius: 5, color: #f1c21b
    Product C: [0.7, 0.2] radius: 6, color: #198038
    Product D: [0.6, 0.3] radius: 5, color: #0f62fe
```

### Example (With Class Styling)

```mermaid
quadrantChart
    title Feature Analysis
    x-axis Low Priority --> High Priority
    y-axis Low Value --> High Value
    quadrant-1 High Priority, High Value
    quadrant-2 Low Priority, High Value
    quadrant-3 Low Priority, Low Value
    quadrant-4 High Priority, Low Value
    Feature A:::highValue: [0.3, 0.9]
    Feature B:::mediumValue: [0.7, 0.6]
    Feature C:::lowValue: [0.2, 0.2]
    Feature D:::highValue: [0.8, 0.8]

    classDef highValue color: #198038, radius: 6
    classDef mediumValue color: #f1c21b, radius: 5
    classDef lowValue color: #da1e28, radius: 4
```

### Example (Business Strategy — BCG Matrix)

```mermaid
quadrantChart
    title Market Analysis
    x-axis Low Market Share --> High Market Share
    y-axis Low Growth --> High Growth
    quadrant-1 Stars
    quadrant-2 Question Marks
    quadrant-3 Dogs
    quadrant-4 Cash Cows
    Product A:::star: [0.8, 0.9]
    Product B:::questionmark: [0.3, 0.7]
    Product C:::dog: [0.2, 0.2]
    Product D:::cashcow: [0.7, 0.3]

    classDef star color: #198038, radius: 6
    classDef questionmark color: #f1c21b, radius: 5
    classDef dog color: #da1e28, radius: 4
    classDef cashcow color: #0f62fe, radius: 5
```

### Example (Multi-line Labels — Hidden-Dot Overlay)

`quadrantChart` does not support line breaks in point labels. Use the hidden-dot overlay technique: each副标签 is a second point at the same X, Y offset by `-0.035`, with `radius: 0` so only its text renders.

```mermaid
quadrantChart
    title 企业数据平台方案谱系定位
    x-axis "低灵活度" --> "高灵活度"
    y-axis "高运维负担" --> "低运维负担"
    quadrant-1 "灵活 + 省心"
    quadrant-2 "省心但不灵活"
    quadrant-3 "运维重且定制弱"
    quadrant-4 "灵活但需自运维"
    "云服务自组装 ": [0.72, 0.3]
    "(本书方案)": [0.72, 0.265] radius: 0
    "云原生一体化 ": [0.25, 0.82]
    "Snowflake/Databricks": [0.25, 0.785] radius: 0
    "湖仓一体开源 ": [0.82, 0.22]
    "Iceberg/Delta+Spark": [0.82, 0.185] radius: 0
    "传统商业数仓 ": [0.15, 0.18]
    "Teradata/Oracle": [0.15, 0.145] radius: 0
    "GCP ": [0.45, 0.68]
    "BigQuery+Dataflow": [0.45, 0.645] radius: 0
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If quadrant charts are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    subgraph Q1["Quadrant 1<br>High X, High Y"]
        A[Feature A]
    end
    subgraph Q2["Quadrant 2<br>Low X, High Y"]
        B[Feature B]
    end
    subgraph Q3["Quadrant 3<br>Low X, Low Y"]
        C[Feature C]
    end
    subgraph Q4["Quadrant 4<br>High X, Low Y"]
        D[Feature D]
    end

    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpWarning fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px

    class A bpSuccess
    class B bpProcess
    class C bpWarning
    class D bpError
```
