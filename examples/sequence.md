## Instructions

Sequence diagrams show interactions between objects or participants over time, displaying the messages exchanged between them.

### Blueprint Styling

Sequence diagrams in Mermaid have limited `classDef` support — use `box` grouping with Blueprint colors to establish semantic context:

```
box rgb(237,245,255) Frontend    — Blueprint Process
box rgb(217,251,251) Backend     — Blueprint Data
box rgb(255,241,241) Error       — Blueprint Error
```

For participant coloring, use inline styling where the renderer supports it, or document the semantic role in the participant label.

Reference: `examples/design-system.md` for the complete Blueprint specification.

### Syntax

- Use `sequenceDiagram` keyword
- Participants: Defined implicitly by order of appearance, or explicitly with `participant Name` or `participant Alias as "Label"`
- Actor symbols: `actor Name` (uses actor symbol instead of rectangle)
- Participant types: `participant`, `actor`, `boundary`, `control`, `entity`, `database`, `collections`, `queue`
- Messages: `Participant1->Participant2: Message` or `Participant1-->>Participant2: Message`
- Arrow types:
  - `->` - Solid line without arrow
  - `-->` - Dotted line without arrow
  - `->>` - Solid line with arrowhead
  - `-->>` - Dotted line with arrowhead
  - `<<->>` - Solid line with bidirectional arrowheads (v11.0.0+)
  - `<<-->>` - Dotted line with bidirectional arrowheads (v11.0.0+)
  - `-x` - Solid line with cross at end
  - `--x` - Dotted line with cross at end
  - `-)` - Solid line with open arrow (async)
  - `--)` - Dotted line with open arrow (async)
- Activations: `activate Participant` and `deactivate Participant`, or use `+`/`-` suffix on arrows
- Notes: `note right of Participant: Text` or `note left of Participant: Text` or `note over Participant1, Participant2: Text`
- Control structures:
  - Loops: `loop Loop text ... end`
  - Alt: `alt Describing text ... else ... end`
  - Opt: `opt Describing text ... end`
  - Parallel: `par [Action 1] ... and [Action 2] ... end`
  - Critical: `critical [Action] ... option [Circumstance] ... end`
  - Break: `break [Condition] ... end`
- Rectangles: `rect rgb(0,0,255) ... end` or `rect rgba(0,0,255,.1) ... end`
- Actor creation/destruction: `create participant Name` or `destroy participant Name` (v10.3.0+)
- Grouping: `box Color Label ... actors ... end`
- Comments: `%% comment` (on separate line)
- Line breaks: Use `\n` in messages and notes
- Sequence numbers: `sequenceNumbers` (optional)

Reference: [Mermaid Sequence Diagram Documentation](https://mermaid.ai/open-source/syntax/sequenceDiagram.html)

### Example (Basic Sequence Diagram)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System
    participant D as Database

    U->>S: Login Request
    activate S
    S->>D: Query User
    activate D
    D-->>S: User Data
    deactivate D
    S-->>U: Login Success
    deactivate S
```

### Example (With Activations - Shortcut)

```mermaid
sequenceDiagram
    participant A as Alice
    participant B as Bob

    A->>+B: Hello
    B-->>-A: Hi
    A->>+B: How are you?
    B-->>-A: I'm good!
```

### Example (With Loops)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System

    U->>S: Request Data
    loop For each item
        S->>S: Process Item
        S-->>U: Return Item
    end
    S-->>U: Complete
```

### Example (With Alt - Alternative Paths)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System

    U->>S: Login Request
    alt Valid credentials
        S-->>U: Login Success
    else Invalid credentials
        S-->>U: Login Failed
    end
```

### Example (With Opt - Optional)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System
    participant C as Cache

    U->>S: Request Data
    opt Cache available
        S->>C: Check Cache
        C-->>S: Cached Data
    end
    S-->>U: Response
```

### Example (With Parallel)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System
    participant A as Service A
    participant B as Service B

    U->>S: Request
    par Parallel Processing
        S->>A: Call Service A
        A-->>S: Response A
    and
        S->>B: Call Service B
        B-->>S: Response B
    end
    S-->>U: Combined Response
```

### Example (With Critical Region)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System

    U->>S: Transaction Request
    critical Critical Transaction
        S->>S: Validate
        S->>S: Process
    option Success
        S-->>U: Success
    option Failure
        S-->>U: Error
    end
```

### Example (With Notes)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System

    U->>S: Request
    note right of S: Processing request
    S->>S: Internal Processing
    note left of U: Waiting for response
    S-->>U: Response
```

### Example (With Actor Creation)

```mermaid
sequenceDiagram
    participant A as Alice
    participant B as Bob

    A->>B: Create Session
    create participant C as Cache
    B->>C: Store Data
    C-->>B: Confirmation
    destroy C
    B-->>A: Session Created
```

### Example (With Grouping — Blueprint Colors)

```mermaid
sequenceDiagram
    box rgb(237,245,255) Frontend
        participant U as User
        participant W as Web App
    end
    box rgb(217,251,251) Backend
        participant A as API
        participant D as Database
    end

    U->>W: Request
    W->>A: API Call
    A->>D: Query
    D-->>A: Data
    A-->>W: Response
    W-->>U: Result
```

### Example (With Different Arrow Types)

```mermaid
sequenceDiagram
    participant A
    participant B

    A->>B: Solid arrow
    A-->>B: Dotted arrow
    A->B: Solid line
    A-->B: Dotted line
    A-xB: Cross end
    A-)B: Async
```

### Example (With Rectangles)

```mermaid
sequenceDiagram
    participant U as User
    participant S as System

    rect rgb(237,245,255)
        U->>S: Request 1
        S-->>U: Response 1
    end
    rect rgba(255, 220, 200, 0.5)
        U->>S: Request 2
        S-->>U: Response 2
    end
```

### Example (API Authentication Flow — Blueprint Style)

```mermaid
sequenceDiagram
    box rgb(237,245,255) Client
        participant Client as Web App
    end
    box rgb(217,251,251) Services
        participant GW as API Gateway
        participant Auth as Auth Service
        participant UserSvc as User Service
        participant DB as Database
    end
    box rgb(242,244,248) External
        participant OAuth as OAuth Provider
    end

    Client->>+GW: POST /login (credentials)
    GW->>+Auth: Validate Credentials
    Auth->>+DB: SELECT user
    DB-->>-Auth: User record
    alt Valid credentials
        Auth->>+OAuth: Request token
        OAuth-->>-Auth: JWT Token
        Auth-->>GW: Token + User
        GW-->>Client: 200 OK + JWT
    else Invalid credentials
        Auth-->>GW: Unauthorized
        GW-->>Client: 401 Unauthorized
    end

    Client->>+GW: GET /users/me (Bearer JWT)
    GW->>+Auth: Verify Token
    Auth-->>-GW: Token valid
    GW->>+UserSvc: Get User Profile
    UserSvc->>+DB: SELECT profile
    DB-->>-UserSvc: Profile data
    UserSvc-->>-GW: User Profile
    GW-->>-Client: 200 OK + Profile
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If sequence diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    Start([Start]) --> User[User]
    User -->|Login Request| System[System]
    System -->|Query| Database[(Database)]
    Database -->|User Data| System
    System -->|Login Success| User
    User --> End([End])
```
