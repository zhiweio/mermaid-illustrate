## Instructions

Flowcharts are composed of nodes (geometric shapes) and edges (arrows or lines). The Mermaid code defines how nodes and edges are made and accommodates different arrow types, multi-directional arrows, and any linking to and from subgraphs.

### Blueprint Styling

All flowchart nodes must use semantic classDef from the Blueprint palette:

```
classDef bpProcess  fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
classDef bpData     fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616
classDef bpSuccess  fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
classDef bpError    fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616
classDef bpExternal fill:#f2f4f8,stroke:#dde1e6,stroke-width:2px,color:#697077
classDef bpUser     fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
classDef bpInfo     fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px,color:#161616
classDef bpGroup    fill:#f2f4f8,stroke:#dde1e6,stroke-width:1px,color:#393939
```

For global theme configuration, use:

```
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#edf5ff','primaryTextColor':'#161616','primaryBorderColor':'#0f62fe','lineColor':'#697077','secondaryColor':'#d9fbfb','tertiaryColor':'#f2f4f8'}}}%%
```

For links, apply semantic styling:
- `linkStyle default stroke:#697077,stroke-width:1.5px` — default
- `linkStyle 0 stroke:#0f62fe,stroke-width:2.5px` — primary flow
- `linkStyle 1 stroke:#007d79,stroke-width:2px,stroke-dasharray:5` — data flow
- `linkStyle 2 stroke:#da1e28,stroke-width:2px` — error path

Reference: `examples/design-system.md` for the complete Blueprint specification.

### Syntax

- Use `flowchart` or `graph` keyword
- Direction: `TD`/`TB` (Top to Bottom), `BT` (Bottom to Top), `RL` (Right to Left), `LR` (Left to Right)
- Node shapes:
  - Default: `A` or `A["Text"]`
  - Round edges: `A("Text")`
  - Stadium: `A(["Text"])`
  - Subroutine: `A[["Text"]]`
  - Cylindrical: `A[("Text")]`
  - Circle: `A(("Text"))`
  - Asymmetric: `A>"Text"]`
  - Rhombus: `A{"Text"}`
  - Hexagon: `A{{"Text"}}`
  - Parallelogram: `A[/"Text"/]` or `A[\"Text"/]`
  - Parallelogram alt: `A[/"Text"\]` or `A[\"Text"\`
  - Trapezoid: `A[/"Text"\]` or `A[\"Text"\`
  - Trapezoid alt: `A[/"Text"/]` or `A[\"Text"/]`
  - Double circle: `A((("Text")))`
  - New shapes (v11.3.0+): `A@{ shape: shapeName }` (e.g., `bang`, `cloud`, `diamond`, `cylinder`, etc.)
- Edges:
  - `A --> B` - Arrow with arrowhead
  - `A --- B` - Open link
  - `A -->|label| B` - Link with label
  - `A -.-> B` - Dotted link
  - `A -.->|label| B` - Dotted link with label
  - `A ==> B` - Thick link
  - `A ==|label|==> B` - Thick link with label
- Subgraphs: `subgraph id ["Title"] ... end`
- Styling: `style A fill:#color,stroke:#color` or `classDef className fill:#color` and `class A className` or `A:::className`
- Links: `linkStyle 0 stroke:#color` (0-based index)
- Comments: `%% comment` (on separate line)
- FontAwesome icons: `A[fa:fa-icon-name]`
- Custom icons: `A[fak:fa-custom-icon-name]` (requires FontAwesome kit)
- Click events: `click A callback "tooltip"` or `click A href "url" "tooltip"`
- Line curves: `curve: basis|bumpX|bumpY|cardinal|catmullRom|linear|monotoneX|monotoneY|natural|step|stepAfter|stepBefore`
- Edge IDs (v11.10.0+): `A -->|label|e1[ID] B` then `e1.curve = "stepBefore"`

**Warnings:**
- If using "end" in a node, capitalize it (e.g., "End" or "END")
- If using "o" or "x" as first letter, add space or capitalize (e.g., "dev--- ops" or "dev---Ops")

Reference: [Mermaid Flowchart Documentation](https://mermaid.ai/open-source/syntax/flowchart.html)

### Example (Basic Flowchart)

```mermaid
flowchart TD
    Start([Start]) --> Process[Process Data]
    Process --> Decision{Valid?}
    Decision -->|Yes| Success[Save]
    Decision -->|No| Error[Error]
    Success --> End([End])
    Error --> End

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px

    class Process bpProcess
    class Decision bpDecision
    class Success bpSuccess
    class Error bpError
```

### Example (With Different Directions)

```mermaid
flowchart LR
    Start([Start]) --> Process[Process] --> End([End])

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class Process bpProcess
```

### Example (With Node Shapes)

```mermaid
flowchart TD
    A[Rectangle]
    B("Rounded")
    C(["Stadium"])
    D[["Subroutine"]]
    E[("Cylindrical")]
    F(("Circle"))
    G>"Asymmetric"]
    H{"Diamond"}
    I{{"Hexagon"}}
    J[/"Parallelogram"/]
    K[\"Parallelogram Alt"\]
    L[/"Trapezoid"\]
    M[\"Trapezoid Alt"/]
    N((("Double Circle")))

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px

    class A,C,D,F,J,K,L,M bpProcess
    class B,E,N bpData
    class H,I bpDecision
```

### Example (With Labels on Edges)

```mermaid
flowchart TD
    Start([Start]) -->|Step 1| Process1[Process 1]
    Process1 -->|Step 2| Process2[Process 2]
    Process2 -->|Step 3| Result[Result]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class Process1,Process2,Result bpProcess
```

### Example (With Subgraphs)

```mermaid
flowchart TD
    Start([Start]) --> B[Process]
    B --> End([End])

    subgraph Group1["Frontend Services"]
        D[Web Server]
        E[API Gateway]
        D --> E
    end

    subgraph Group2["Backend Services"]
        F[Auth Service]
        G[User Service]
        F --> G
    end

    B --> D
    E --> F
    G --> End

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class B,D,E,F,G bpProcess
```

### Example (With Styling)

```mermaid
flowchart TD
    A[Start] --> B[Process]
    B --> C[End]

    style A fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    style B fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    style C fill:#defbe6,stroke:#198038,stroke-width:2px
```

### Example (With Class Definitions)

```mermaid
flowchart TD
    A[Start] --> B[Process]
    B --> C[End]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px

    class A,C bpSuccess
    class B bpProcess
```

### Example (With Class Shorthand)

```mermaid
flowchart TD
    A[Start]:::bpStart --> B[Process]:::bpProcess
    B --> C[End]:::bpEnd

    classDef bpStart fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpEnd fill:#defbe6,stroke:#198038,stroke-width:2px
```

### Example (With Dotted Links)

```mermaid
flowchart TD
    Primary[Primary Flow] --> Success[Success]
    Primary -.-> Alt[Alternative Flow]
    Alt -.->|Optional| Fallback[Fallback]
    Fallback -.-> Success

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px

    class Primary,Alt bpProcess
    class Success bpSuccess
    class Fallback bpDecision
```

### Example (With Thick Links)

```mermaid
flowchart TD
    A[Start] ==> B[Critical Process]
    B ==>|Critical| C[End]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class A,B,C bpProcess
```

### Example (Complex Flowchart)

```mermaid
flowchart TD
    Start([Start]) --> Input{Input Data?}
    Input -->|Yes| Validate[Validate Data]
    Input -->|No| End([End])

    Validate --> Check{Valid?}
    Check -->|Yes| Process[Process Data]
    Check -->|No| Error[Error Handler]

    Process --> Save[Save Results]
    Save --> End
    Error --> End

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px

    class Validate,Process,Save bpProcess
    class Input,Check bpDecision
    class Start,End bpSuccess
    class Error bpError
```

### Example (With Multiple Paths)

```mermaid
flowchart TD
    A[Start] --> B{Decision}
    B -->|Path 1| C[Process 1]
    B -->|Path 2| D[Process 2]
    B -->|Path 3| E[Process 3]

    C --> F[Converge]
    D --> F
    E --> F
    F --> G[End]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px

    class A,C,D,E,F,G bpProcess
    class B bpDecision
```

### Example (With Edge Styling)

```mermaid
flowchart TD
    A[Start] --> B[Process 1]
    B --> C[Process 2]
    C --> D[End]

    linkStyle 0 stroke:#0f62fe,stroke-width:2.5px
    linkStyle 1 stroke:#697077,stroke-width:1.5px
    linkStyle 2 stroke:#198038,stroke-width:2px

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class A,B,C,D bpProcess
```

### Example (With New Shapes - v11.3.0+)

```mermaid
flowchart TD
    A@{ shape: cloud, label: "Cloud Service" }
    B@{ shape: diam, label: "Decision" }
    C@{ shape: cyl, label: "Database" }
    D@{ shape: bang, label: "Event" }

    A --> B
    B --> C
    C --> D

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px
    classDef bpInfo fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px

    class A bpProcess
    class B bpDecision
    class C bpData
    class D bpInfo
```

### Example (With Edge IDs and Curve Styles - v11.10.0+)

```mermaid
flowchart LR
    A[Start]
    B[Process]
    C[End]
    A e1@-->|Step 1| B
    B e2@-->|Step 2| C

    e1@{ curve: stepBefore }
    e2@{ curve: stepAfter }

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class A,B,C bpProcess
```

### Example (Microservice Architecture — Blueprint Style)

This is a production-grade architecture diagram using the full Blueprint palette:

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#edf5ff','primaryTextColor':'#161616','primaryBorderColor':'#0f62fe','lineColor':'#697077','secondaryColor':'#d9fbfb','tertiaryColor':'#f2f4f8'}}}%%
flowchart TD
    subgraph Edge["Edge & Client"]
        CDN[CDN]
        Client[Web Client]
    end

    subgraph Gateway["API Gateway Layer"]
        GW[API Gateway]
    end

    subgraph Core["Core Services"]
        Auth[Auth Service]
        User[User Service]
        Order[Order Service]
        Pay[Payment Service]
        Notify[Notification Service]
    end

    subgraph Data["Data Layer"]
        DB[(Primary DB)]
        Cache[(Redis Cache)]
        Queue[(Message Queue)]
        Search[(Search Engine)]
    end

    subgraph External["External Services"]
        PayGW[Payment Gateway]
        Email[Email Provider]
    end

    Client --> CDN
    CDN --> GW
    GW --> Auth
    GW --> User
    GW --> Order
    User --> Auth
    Order --> Pay
    Order --> Notify
    Pay --> PayGW
    Pay --> Cache
    Notify --> Email
    Notify --> Queue
    Auth --> DB
    User --> DB
    Order --> DB
    Order --> Search
    Pay --> DB

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px
    classDef bpExternal fill:#f2f4f8,stroke:#dde1e6,stroke-width:2px,color:#697077

    class CDN,Client,GW,Auth,User,Order,Pay,Notify bpProcess
    class DB,Cache,Queue,Search bpData
    class PayGW,Email bpExternal
```

### Example (CI/CD Pipeline)

```mermaid
flowchart LR
    Code[Push Code] --> Build[Build]
    Build --> Test{Unit Tests}
    Test -->|Pass| Lint[Lint & SAST]
    Test -->|Fail| Notify1[Notify Developer]
    Lint -->|Pass| DeployStg[Deploy Staging]
    Lint -->|Fail| Notify1
    DeployStg --> E2E{E2E Tests}
    E2E -->|Pass| DeployProd[Deploy Production]
    E2E -->|Fail| Rollback[Rollback]
    DeployProd --> Monitor[Health Check]
    Monitor -->|OK| Done([Done])
    Monitor -->|Fail| Rollback

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    classDef bpDecision fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px

    class Code,Build,Lint,DeployStg,DeployProd,Monitor bpProcess
    class Test,E2E bpDecision
    class Done bpSuccess
    class Notify1,Rollback bpError
```
