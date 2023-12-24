- [SOLID](#solid)
  - [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
  - [Open-Closed Principle (OCP)](#open-closed-principle-ocp)
  - [Liskov Substitution Principle (LSP):](#liskov-substitution-principle-lsp)
  - [Interface Segregation Principle (ISP):](#interface-segregation-principle-isp)
  - [Dependency Inversion Principle (DIP):](#dependency-inversion-principle-dip)


# SOLID
## Single Responsibility Principle (SRP)
One class one responsibility.

## Open-Closed Principle (OCP)
If you want to modify the software entities (classes, modules, functions), use subclass or create new entities instead of modifying the existing one.

**Example**: Let's say you have a class called `Shape` with a method `calculateArea()`, which calculates the area of the shape. According to the OCP, you should not modify the `Shape` class to add new shape types or modify the existing logic for calculating the area.

Instead, you can extend the `Shape` class to create new shape classes (e.g., `Circle`, `Rectangle`, `Triangle`) and override the `calculateArea()` method in each subclass with the specific logic for that shape. This way, you are extending the functionality of the `Shape` class without modifying its implementation.

## Liskov Substitution Principle (LSP):
The object of its subclasses could substitute the object of its superclass.

**Example**:
```javascript
class Shape {
    constructor() {}

    calculateArea() {
        // Common implementation for calculating area
    }
}

class Rectangle extends Shape {
    constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
}

    calculateArea() {
        return this.width * this.height;
    }
}

class Square extends Shape {
    constructor(sideLength) {
    super();
    this.sideLength = sideLength;
}

    calculateArea() {
        return this.sideLength * this.sideLength;
    }
}
```

In this example, we have a base class `Shape` that defines a common method `calculateArea()` for calculating the area of a shape. The Rectangle and `Square` classes inherit from `Shape` and provide their own implementations of the `calculateArea()` method.

Now, let's see how the LSP holds by substituting objects of the derived classes (`Rectangle` and `Square`) for the base class (`Shape`):

```javascript
function printArea(shape) {
    console.log(`Area: ${shape.calculateArea()}`);
}

const rectangle = new Rectangle(4, 6);
printArea(rectangle); // Output: Area: 24

const square = new Square(5);
printArea(square); // Output: Area: 25
```

In the `printArea()` function, we accept an object of the `Shape` base class. However, we can safely substitute it with objects of its derived classes (`Rectangle` and `Square`). This demonstrates the Liskov Substitution Principle, as substituting `Rectangle` or `Square` for `Shape` does not break the correctness of the program.

## Interface Segregation Principle (ISP):

Interface should be smaller so that the client shouldn't have to depend on redundant interface. Let's consider an example with a messaging system where we have an `IMessage` interface representing a generic message:

```javascript
interface IMessage {
    send(): void;
    receive(): void;
    save(): void;
}
```

In this initial design, the `IMessage` interface has three methods: `send()`, `receive()`, and `save()`. However, some client classes may only need to send and receive messages, while others may only need to save messages. Following the ISP, we can segregate the interface into smaller interfaces that cater to specific client needs:

```javascript
interface ISender {
    send(): void;
    receive(): void;
}

interface ISaver {
    save(): void;
}
```

Now, we have two separate interfaces: `ISender`, which includes the `send()` and `receive()` methods, and `ISaver`, which includes the `save()` method. This segregation allows clients to depend only on the interfaces they require.

## Dependency Inversion Principle (DIP):

High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

Without applying the Dependency Inversion Principle:

```java
class Database {
    public String getData() {
        // Code to fetch data from the database
        return "Data from the database";
    }
}

class ReportGenerator {
    private Database database;

    public ReportGenerator() {
        this.database = new Database();
    }

    public void generateReport() {
        String data = this.database.getData();
        // Code to generate the report using the fetched data
        System.out.println("Generated report with data: " + data);
    }
}
```

In this non-compliant example, `ReportGenerator` depends directly on the concrete `Database` class.

Applying the Dependency Inversion Principle using abstraction (interfaces or abstract classes):

```java
// The abstraction
interface DataProvider {
    String getData();
}

// Both Database and ReportGenerator depends on the abstraction interface DataProvider
class Database implements DataProvider {
    @Override
    public String getData() {
        // Code to fetch data from the database
        return "Data from the database";
    }
}

// Both Database and ReportGenerator depends on the abstraction interface DataProvider
class ReportGenerator {
    private DataProvider dataProvider;

    public ReportGenerator(DataProvider dataProvider) {
        this.dataProvider = dataProvider;
    }

    public void generateReport() {
        String data = this.dataProvider.getData();
        // Code to generate the report using the fetched data
        System.out.println("Generated report with data: " + data);
    }
}

```

In this compliant example, the `DataProvider` interface is simulated by using a class with a method that throws an error. Both `Database` and any potential future data sources can extend this class. The `ReportGenerator` class now depends on the abstraction (`DataProvider`) rather than the concrete `Database` class directly, adhering to the Dependency Inversion Principle.


There is [a comparison between DIP and DI](../Design_Pattern/readme.md#dependency-injection-di-vs-dependency-inversion-principle-dip).