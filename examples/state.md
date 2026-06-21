## Instructions

State diagrams show the different states of an object and the transitions between them, useful for modeling state machines.

### Blueprint Styling

State diagrams use `classDef` + `class` for semantic coloring:

```
classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616
classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
classDef bpWarning fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616
```

Apply to states by their ID: `class StateName bpProcess`

See `examples/design-system.md` for the canonical palette, classDef templates, and themeVariables.

### Syntax

- Use `stateDiagram-v2` (recommended) or `stateDiagram` keyword
- States: `[StateName]` or `state StateName` or `StateId : State Description`
- Initial state: `[*]` (start state)
- Final state: `[*]` (end state)
- Transitions: `State1 --> State2 : Event` or `State1 --> State2`
- Composite states: `state StateName { [State1] [State2] }`
- Choice: `<<choice>>` (decision point)
- Fork/Join: `<<fork>>` and `<<join>>`
- Notes: `note right of StateName : Note text` or `note left of StateName : Note text`
- Concurrency: `--` (parallel states)
- Direction: `direction TB|BT|LR|RL` (default: TB)
- Comments: `%% comment` (on separate line)
- Styling: `classDef className fill:#color,stroke:#color` and `class StateName className` or `StateName:::className`
- Spaces in state names: Define state with id first, then reference it

Reference: [Mermaid State Diagram Documentation](https://mermaid.ai/open-source/syntax/stateDiagram.html)

### Example (Basic State Diagram)

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing : Start
    Processing --> Completed : Success
    Processing --> Error : Failure
    Error --> Idle : Retry
    Completed --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616

    class Idle,Processing bpProcess
    class Completed bpSuccess
    class Error bpError
```

### Example (With State Descriptions)

```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> Moving : Start
    Moving --> Still : Stop
    Moving --> Crash : Error
    Crash --> [*]

    state Still {
        [*] --> Stationary
        Stationary --> [*]
    }

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616

    class Still,Moving,Stationary bpProcess
    class Crash bpError
```

### Example (With Transitions and Labels)

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Running : Start Event
    Running --> Paused : Pause Event
    Paused --> Running : Resume Event
    Running --> Stopped : Stop Event
    Stopped --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616

    class Idle,Running,Paused bpProcess
    class Stopped bpSuccess
```

### Example (Composite States)

```mermaid
stateDiagram-v2
    [*] --> First

    state First {
        [*] --> State1
        State1 --> State2
        State2 --> [*]
    }

    First --> Second

    state Second {
        [*] --> State3
        State3 --> State4
        State4 --> [*]
    }

    Second --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class First,Second bpProcess
```

### Example (With Choice)

```mermaid
stateDiagram-v2
    [*] --> State1
    State1 --> Choice1 : Event1
    Choice1 --> State2 : Condition1
    Choice1 --> State3 : Condition2
    State2 --> [*]
    State3 --> [*]

    state Choice1 <<choice>>

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616

    class State1,State2,State3 bpProcess
    class State2 bpSuccess
```

### Example (With Fork and Join)

```mermaid
stateDiagram-v2
    [*] --> Fork1

    state Fork1 <<fork>>
    Fork1 --> State1
    Fork1 --> State2
    Fork1 --> State3

    State1 --> Join1
    State2 --> Join1
    State3 --> Join1

    state Join1 <<join>>
    Join1 --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class State1,State2,State3 bpProcess
```

### Example (With Notes)

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing : Start
    Processing --> Completed : Success
    Completed --> [*]

    note right of Processing : Critical state — timeout after 30s
    note left of Idle : Initial state — always reachable

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616

    class Idle,Processing bpProcess
    class Completed bpSuccess
```

### Example (With Concurrency)

```mermaid
stateDiagram-v2
    [*] --> State1
    State1 --> State2
    State2 --> State3

    State2 --> Parallel1
    State2 --> Parallel2

    Parallel1 --> State4
    Parallel2 --> State5

    State4 --> State3
    State5 --> State3
    State3 --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class State1,State2,State3,State4,State5,Parallel1,Parallel2 bpProcess
```

### Example (With Direction - Left to Right)

```mermaid
stateDiagram-v2
    direction LR
    [*] --> State1
    State1 --> State2 : Event
    State2 --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class State1,State2 bpProcess
```

### Example (Order Lifecycle — Blueprint Style)

```mermaid
stateDiagram-v2
    [*] --> Created
    Created --> Confirmed : Customer confirms
    Confirmed --> Paid : Payment received
    Confirmed --> Cancelled : Payment timeout
    Paid --> Shipped : Warehouse dispatches
    Shipped --> Delivered : Carrier delivers
    Shipped --> Lost : Lost in transit
    Delivered --> Returned : Customer returns
    Returned --> Refunded : Refund processed
    Paid --> Refunded : Cancellation refund
    Delivered --> [*]
    Cancelled --> [*]
    Refunded --> [*]
    Lost --> [*]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616
    classDef bpWarning fill:#fcf4d6,stroke:#f1c21b,stroke-width:2px,color:#161616

    class Created,Confirmed,Paid,Shipped bpProcess
    class Delivered bpSuccess
    class Cancelled,Lost bpError
    class Returned,Refunded bpWarning
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If state diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    Start([Start]) --> Idle[Idle]
    Idle -->|Start| Processing[Processing]
    Processing -->|Success| Completed[Completed]
    Processing -->|Failure| Error[Error]
    Error -->|Retry| Idle
    Completed --> End([End])

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpSuccess fill:#defbe6,stroke:#198038,stroke-width:2px,color:#161616
    classDef bpError fill:#fff1f1,stroke:#da1e28,stroke-width:2px,color:#161616

    class Idle,Processing bpProcess
    class Completed bpSuccess
    class Error bpError
```
