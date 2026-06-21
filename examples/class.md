## Instructions

Class diagrams represent the structure of a system by showing classes, their attributes, methods, and relationships.

### Blueprint Styling

Class diagrams use `cssClass` for styling (note the different function name vs. flowchart's `class`):

```
classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616
classDef bpInterface fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px,color:#161616
classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
```

Apply with `cssClass "ClassName" className`.

See `examples/design-system.md` for the canonical palette, classDef templates, and themeVariables.

### Syntax

- Use `classDiagram` keyword
- Class definition: `class ClassName` or via relationship `Vehicle <|-- Car`
- Members: `ClassName : +attribute` or `ClassName { +attribute +method() }`
- Visibility: `+` (Public), `-` (Private), `#` (Protected), `~` (Package/Internal)
- Methods: Identified by `()` parentheses
- Return types: `method() ReturnType` (space between `)` and return type)
- Generic types: `ClassName~Type~` (enclosed in `~` tilde)
- Classifiers: `*` (Abstract), `$` (Static)
- Relationships:
  - `<|--` - Inheritance
  - `*--` - Composition
  - `o--` - Aggregation
  - `-->` - Association
  - `--` - Link (Solid)
  - `..>` - Dependency
  - `..|>` - Realization
  - `..` - Link (Dashed)
- Labels: `ClassA --> ClassB : LabelText`
- Cardinality: `"1" ClassA --> "0..1" ClassB : LabelText`
- Annotations: `<<Interface>>`, `<<Abstract>>`, `<<Service>>`, `<<Enumeration>>`
- Interfaces: `ClassA ..|> InterfaceName` or lollipop syntax
- Namespaces: `namespace NamespaceName { Class1 Class2 }`
- Direction: `direction TB|BT|LR|RL` (default: TB)
- Comments: `%% comment` (on separate line)
- Notes: `note for ClassName "note text"`
- Styling: `style ClassName fill:#color,stroke:#color` or `classDef className fill:#color` and `cssClass "ClassName" className` or `ClassName:::className`

Reference: [Mermaid Class Diagram Documentation](https://mermaid.ai/open-source/syntax/classDiagram.html)

### Example (Basic Class Diagram)

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +eat()
        +sleep()
    }
    class Dog {
        +String breed
        +bark()
    }
    class Cat {
        +meow()
    }

    Animal <|-- Dog
    Animal <|-- Cat

    classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616

    cssClass "Animal" bpAbstract
    cssClass "Dog,Cat" bpProcess
```

### Example (With Visibility and Methods)

```mermaid
classDiagram
    class BankAccount {
        -double balance
        +deposit(amount)
        +withdraw(amount) double
        +getBalance() double
    }
    class Customer {
        +String name
        +String email
        +openAccount() BankAccount
    }

    Customer --> BankAccount : owns

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "BankAccount,Customer" bpProcess
```

### Example (With Return Types)

```mermaid
classDiagram
    class Calculator {
        +add(a, b) int
        +subtract(a, b) int
        +multiply(a, b) int
        +divide(a, b) double
    }

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "Calculator" bpProcess
```

### Example (With Generic Types)

```mermaid
classDiagram
    class List~T~ {
        +add(item T)
        +get(index) T
        +size() int
    }
    class Map~K,V~ {
        +put(key K, value V)
        +get(key K) V
    }

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "List,Map" bpProcess
```

### Example (With Relationships)

```mermaid
classDiagram
    class Vehicle {
        +String brand
        +start()
    }
    class Car {
        +int doors
    }
    class Engine {
        +int horsepower
    }
    class Wheel {
        +int size
    }

    Vehicle <|-- Car
    Car *-- Engine
    Car o-- Wheel

    classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "Vehicle" bpAbstract
    cssClass "Car,Engine,Wheel" bpProcess
```

### Example (With Labels and Cardinality)

```mermaid
classDiagram
    class Company {
        +String name
    }
    class Employee {
        +String name
        +String position
    }

    Company "1" --> "1..*" Employee : employs

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "Company,Employee" bpProcess
```

### Example (With Interfaces)

```mermaid
classDiagram
    class Shape {
        <<interface>>
        +area() double
        +perimeter() double
    }
    class Circle {
        +double radius
        +area() double
        +perimeter() double
    }
    class Rectangle {
        +double width
        +double height
        +area() double
        +perimeter() double
    }

    Shape <|.. Circle
    Shape <|.. Rectangle

    classDef bpInterface fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "Shape" bpInterface
    cssClass "Circle,Rectangle" bpProcess
```

### Example (With Annotations)

```mermaid
classDiagram
    class UserService {
        <<Service>>
        +createUser()
        +deleteUser()
    }
    class AbstractRepository {
        <<Abstract>>
        +save()
        +find()*
    }
    class Status {
        <<Enumeration>>
        ACTIVE
        INACTIVE
        PENDING
    }

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
    classDef bpInfo fill:#f6f2ff,stroke:#8a3ffc,stroke-width:2px,color:#161616
    cssClass "UserService" bpProcess
    cssClass "AbstractRepository" bpAbstract
    cssClass "Status" bpInfo
```

### Example (With Namespaces)

```mermaid
classDiagram
    namespace Core {
        class User
        class Product
    }
    namespace Services {
        class UserService
        class ProductService
    }

    User --> UserService
    Product --> ProductService

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "User,Product,UserService,ProductService" bpProcess
```

### Example (With Direction - Left to Right)

```mermaid
classDiagram
    direction LR
    class Animal {
        +String name
        +eat()
    }
    class Dog {
        +bark()
    }
    Animal <|-- Dog

    classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    cssClass "Animal" bpAbstract
    cssClass "Dog" bpProcess
```

### Example (Complex Class Diagram — Blueprint Style)

```mermaid
classDiagram
    class Person {
        +String name
        +int age
        +walk()
    }
    class Student {
        +int studentId
        +study()
    }
    class Teacher {
        +String subject
        +teach()
    }
    class Course {
        +String title
        +int credits
    }
    class Enrollment {
        +date enrolledDate
        +String grade
    }

    Person <|-- Student
    Person <|-- Teacher
    Student "1..*" --> "0..*" Course : enrolls
    Course "1" --> "0..*" Enrollment : has
    Student "1" --> "0..*" Enrollment : receives

    classDef bpAbstract fill:#f2f4f8,stroke:#697077,stroke-width:2px,color:#161616
    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    classDef bpData fill:#d9fbfb,stroke:#007d79,stroke-width:2px,color:#161616

    cssClass "Person" bpAbstract
    cssClass "Student,Teacher,Course" bpProcess
    cssClass "Enrollment" bpData
```

### Alternative (Flowchart - compatible with all Mermaid versions)

If class diagrams are not supported, use this flowchart alternative:

```mermaid
flowchart TD
    Animal[Animal]
    Dog[Dog]
    Cat[Cat]

    Animal -->|inherits| Dog
    Animal -->|inherits| Cat

    classDef bpProcess fill:#edf5ff,stroke:#0f62fe,stroke-width:2px,color:#161616
    class Animal,Dog,Cat bpProcess
```
