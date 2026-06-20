## Instructions

Timeline diagrams display events in chronological order, showing the sequence of events over time.

**Note**: This is an experimental diagram type. The syntax and properties can change in future releases. The syntax is stable except for the icon integration which is the experimental part.

### Blueprint Styling

Timeline diagrams have limited built-in styling. Structure events to convey semantic meaning through labeling conventions.

### Syntax

- Use `timeline` keyword
- Title: `title Timeline Title` (optional)
- Time period: `{time period} : {event}` or `{time period} : {event} : {event}` (multiple events per period)
- Sections: `section Section Name` (groups time periods in sections/ages)
- Text wrapping: Use `<br>` to force line breaks
- Multiple events per period: Can be on same line with `:` separator or on separate lines

Reference: [Mermaid Timeline Diagram Documentation](https://mermaid.ai/open-source/syntax/timeline.html)

### Example (Basic Timeline)

```mermaid
timeline
    title Project Milestones
    2024 Q1 : Project Kickoff : Team formation
    2024 Q2 : Development Phase 1 : First Release
    2024 Q3 : Development Phase 2 : Production Launch
```

### Example (With Sections)

```mermaid
timeline
    title Product Development Timeline
    section 2024 Q1
        Project Kickoff : Team formation
        Requirements Gathering : Stakeholder meetings
    section 2024 Q2
        Development Phase 1 : Core features
        First Release : Beta version
    section 2024 Q3
        Development Phase 2 : Advanced features
        Production Launch : Public release
```

### Example (Multiple Events per Period)

```mermaid
timeline
    title Company History
    2020 : Founded : First Product Launch
    2021 : Series A Funding : Team Expansion
    2022 : International Expansion : Second Product Launch
    2023 : Series B Funding : Major Partnership
```

### Example (With Text Wrapping)

```mermaid
timeline
    title Long Event Names
    2024 Q1 : Project Kickoff and<br>Team Formation
    2024 Q2 : Development Phase 1<br>Core Features Implementation
    2024 Q3 : Production Launch<br>Public Release
```

### Example (Historical Timeline)

```mermaid
timeline
    title Technology Evolution
    section 1990s
        Early Internet : Web 1.0
    section 2000s
        Social Media : Web 2.0
    section 2010s
        Mobile Revolution : Cloud Computing
    section 2020s
        AI & Machine Learning : Web 3.0
```

### Example (Release Cycles)

```mermaid
timeline
    title Release Schedule
    section Alpha
        Jan 2024 : v0.1 — Core engine : v0.2 — Basic UI
    section Beta
        Mar 2024 : v0.3 — Feature complete : v0.4 — Performance tuning
    section Release
        Apr 2024 : v1.0 — GA Release : v1.1 — Bug fixes
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If timeline diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart LR
    Start[2024 Q1<br>Project Kickoff] --> Phase1[2024 Q2<br>Development Phase 1]
    Phase1 --> Phase2[2024 Q3<br>Development Phase 2]
    Phase2 --> Launch[2024 Q4<br>Production Launch]

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px
    class Start,Phase1,Phase2,Launch bpProcess
```
