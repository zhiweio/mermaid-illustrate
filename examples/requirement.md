## Instructions

Requirement diagrams model system requirements and their relationships, showing how requirements relate to each other and to system elements. The modeling specs follow those defined by SysML v1.6.

### Blueprint Styling

Requirement diagrams use `style` and `classDef` + `class` for entity styling. Map risk levels to Blueprint colors:

- `High` risk → `#da1e28` (Error Red)
- `Medium` risk → `#f1c21b` (Warning Amber)
- `Low` risk → `#198038` (Success Green)

### Syntax

- Use `requirementDiagram` keyword
- Requirements: `<type> name { id: id, text: text, risk: risk, verifymethod: method }`
- Requirement types: `requirement`, `functionalRequirement`, `interfaceRequirement`, `performanceRequirement`, `physicalRequirement`, `designConstraint`
- Risk levels: `Low`, `Medium`, `High`
- Verification methods: `Analysis`, `Inspection`, `Test`, `Demonstration`
- Elements: `element name { type: type, docref: docref }`
- Relationships: Must use arrow syntax `Source - <relationship> -> Destination`
  - `contains` - Parent-child relationship
  - `copies` - Requirement copies another
  - `derives` - Requirement derives from another
  - `satisfies` - Requirement satisfies element
  - `verifies` - Element verifies requirement
  - `refines` - Requirement refines another
  - `traces` - Trace relationship
- Direction: `direction TB|BT|LR|RL` (default: TB)
- Styling: `style name fill:#color,stroke:#color` or `classDef className fill:#color`

Reference: [Mermaid Requirement Diagram Documentation](https://mermaid.ai/open-source/syntax/requirementDiagram.html)

### Example (Basic Requirement Diagram)

```mermaid
requirementDiagram
    requirement R1 {
        id: 1
        text: System must handle 1000 concurrent users
        risk: high
        verifymethod: test
    }
    requirement R2 {
        id: 2
        text: System must respond within 2 seconds
        risk: medium
        verifymethod: test
    }

    element E1 {
        type: System
        docref: docs/system.md
    }

    R1 - satisfies -> E1
    R2 - satisfies -> E1

    style R1 fill:#fff1f1,stroke:#da1e28,stroke-width:2px
    style R2 fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    style E1 fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
```

### Example (With Different Requirement Types)

```mermaid
requirementDiagram
    functionalRequirement FR1 {
        id: 1
        text: User authentication functionality
        risk: high
        verifymethod: test
    }
    performanceRequirement PR1 {
        id: 2
        text: Response time must be under 2 seconds
        risk: medium
        verifymethod: analysis
    }
    interfaceRequirement IR1 {
        id: 3
        text: REST API interface specification
        risk: low
        verifymethod: inspection
    }

    FR1 - refines -> PR1
    PR1 - traces -> IR1

    style FR1 fill:#fff1f1,stroke:#da1e28,stroke-width:2px
    style PR1 fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    style IR1 fill:#defbe6,stroke:#198038,stroke-width:2px
```

### Example (With Relationships)

```mermaid
requirementDiagram
    requirement R1 {
        id: 1
        text: High-level system requirement
        risk: high
        verifymethod: test
    }
    requirement R2 {
        id: 2
        text: Detailed requirement
        risk: medium
        verifymethod: test
    }
    requirement R3 {
        id: 3
        text: Derived requirement
        risk: low
        verifymethod: analysis
    }

    element E1 {
        type: Component
        docref: docs/component.md
    }

    R1 - contains -> R2
    R2 - refines -> R1
    R3 - derives -> R1
    R2 - satisfies -> E1
    E1 - verifies -> R2

    classDef highRisk fill:#fff1f1,stroke:#da1e28,stroke-width:2px
    classDef mediumRisk fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef lowRisk fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef element fill:#edf5ff,stroke:#0f62fe,stroke-width:2px

    class R1 highRisk
    class R2 mediumRisk
    class R3 lowRisk
    class E1 element
```

### Example (With Direction - Left to Right)

```mermaid
requirementDiagram
    direction LR

    requirement R1 {
        id: 1
        text: Requirement 1
        risk: high
        verifymethod: test
    }
    requirement R2 {
        id: 2
        text: Requirement 2
        risk: medium
        verifymethod: test
    }

    R1 - refines -> R2

    style R1 fill:#fff1f1,stroke:#da1e28,stroke-width:2px
    style R2 fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If requirement diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    R1[Requirement 1<br>Risk: High]
    R2[Requirement 2<br>Risk: Medium]
    E1[Element 1<br>Type: System]

    R1 -->|satisfies| E1
    R2 -->|satisfies| E1

    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616
    classDef bpWarning fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616

    class R1 bpError
    class R2 bpWarning
    class E1 bpProcess
```
