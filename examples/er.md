## Instructions

Entity Relationship (ER) diagrams represent the structure of a database, showing entities, their attributes, and relationships between them.

### Blueprint Styling

ER diagrams use `classDef` + `class` with entity names:

```
classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
classDef bpJoin fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
classDef bpExternal fill:#f2f4f8,stroke:#dde1e6,stroke-width:2px,color:#525252
```

See `examples/design-system.md` for the canonical palette, classDef templates, and themeVariables.

### Syntax

- Use `erDiagram` keyword
- Entities: `ENTITY_NAME { }` or `ENTITY_NAME { type name }` (with attributes)
- Relationships: `<first-entity> [<relationship> <second-entity> : <relationship-label>]`
- Cardinality markers:
  - `||` - Exactly one
  - `|o` - Zero or one
  - `}|` - One or more
  - `}o` - Zero or more
- Relationship types:
  - `--` - Identifying relationship (solid line)
  - `..` - Non-identifying relationship (dashed line)
- Aliases: `one or zero`, `zero or one`, `one or more`, `one or many`, `many(1)`, `1+`, `zero or more`, `zero or many`, `many(0)`, `0+`, `only one`, `1`, `to`, `optionally to`
- Attributes: `type name` or `*type name` (asterisk for primary key)
- Attribute keys: `PK` (Primary Key), `FK` (Foreign Key), `UK` (Unique Key)
- Comments: Double quotes at the end of attribute: `type name "comment"`
- Entity aliases: `ENTITY_NAME[alias]` (alias shown instead of entity name)
- Direction: `direction TB|BT|LR|RL` (default: TB)
- Styling: `style entityId fill:#color,stroke:#color` or `classDef className fill:#color`
- Unicode and Markdown: Supported in entity names, relationships, and attributes

Reference: [Mermaid Entity Relationship Diagram Documentation](https://mermaid.ai/open-source/syntax/entityRelationshipDiagram.html)

### Example (Basic ER Diagram)

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    PRODUCT ||--|{ LINE-ITEM : "ordered in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class CUSTOMER,ORDER,PRODUCT,LINE-ITEM bpEntity
```

### Example (With Attributes)

```mermaid
erDiagram
    CUSTOMER {
        int id PK
        string name
        string email UK
        string phone
    }
    ORDER {
        int id PK
        date orderDate
        decimal total
        int customerId FK
    }
    PRODUCT {
        int id PK
        string name
        decimal price
        int stock
    }
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    PRODUCT ||--|{ LINE-ITEM : "ordered in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class CUSTOMER,ORDER,PRODUCT bpEntity
```

### Example (With Relationship Labels)

```mermaid
erDiagram
    PROPERTY ||--|{ ROOM : contains
    ROOM ||--o{ WINDOW : has
    BUILDING ||--o{ PROPERTY : "located in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class PROPERTY,ROOM,WINDOW,BUILDING bpEntity
```

### Example (Identifying vs Non-identifying)

```mermaid
erDiagram
    PERSON }|..|{ CAR : "driver"
    PERSON ||--o{ NAMED-DRIVER : "is"
    CAR ||--o{ NAMED-DRIVER : "drives"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpJoin fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
    class PERSON,CAR bpEntity
    class NAMED-DRIVER bpJoin
```

### Example (With Aliases)

```mermaid
erDiagram
    CUSTOMER[Cust] ||--o{ ORDER[Ord] : places
    ORDER ||--|{ LINE-ITEM[Item] : contains
    PRODUCT[Prod] ||--|{ LINE-ITEM : "ordered in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class CUSTOMER,ORDER,PRODUCT,LINE-ITEM bpEntity
```

### Example (With Attribute Comments)

```mermaid
erDiagram
    USER {
        int id PK "Unique identifier"
        string username UK "Login name"
        string email "Contact email"
        date createdAt "Account creation date"
    }
    POST {
        int id PK
        string title
        text content
        int userId FK "Author reference"
        date publishedAt
    }
    USER ||--o{ POST : "writes"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class USER,POST bpEntity
```

### Example (With Direction - Left to Right)

```mermaid
erDiagram
    direction LR
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    PRODUCT ||--|{ LINE-ITEM : "ordered in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class CUSTOMER,ORDER,PRODUCT,LINE-ITEM bpEntity
```

### Example (Complex Database Schema — Blueprint Style)

```mermaid
erDiagram
    USER {
        int id PK
        string username UK
        string email
        date createdAt
    }
    POST {
        int id PK
        string title
        text content
        int authorId FK
        date publishedAt
    }
    COMMENT {
        int id PK
        text content
        int postId FK
        int userId FK
        date createdAt
    }
    CATEGORY {
        int id PK
        string name
        string slug UK
    }
    TAG {
        int id PK
        string name UK
    }
    POST_TAG {
        int postId FK
        int tagId FK
    }

    USER ||--o{ POST : "writes"
    POST ||--o{ COMMENT : "has"
    USER ||--o{ COMMENT : "makes"
    CATEGORY ||--o{ POST : "categorizes"
    POST ||--o{ POST_TAG : "tagged with"
    TAG ||--o{ POST_TAG : "used in"

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpJoin fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
    class USER,POST,COMMENT,CATEGORY,TAG bpEntity
    class POST_TAG bpJoin
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If ER diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    CUSTOMER[Customer]
    ORDER[Order]
    PRODUCT[Product]
    LINE_ITEM[Line Item]

    CUSTOMER -->|places| ORDER
    ORDER -->|contains| LINE_ITEM
    PRODUCT -->|ordered in| LINE_ITEM

    classDef bpEntity fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class CUSTOMER,ORDER,PRODUCT,LINE_ITEM bpEntity
```
