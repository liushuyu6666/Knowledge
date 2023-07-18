- [SOLID](#solid)


# SOLID
1. Single Responsibility Principle (SRP): 
   One class one responsibility.
2. Open-Closed Principle (OCP): 
   If you want to modify the software entities (classes, modules, functions), use subclass or create new entities instead of modifying the existing one.
   **Example**: Let's say you have a class called `Shape` with a method `calculateArea()`, which calculates the area of the shape. According to the OCP, you should not modify the `Shape` class to add new shape types or modify the existing logic for calculating the area.
   Instead, you can extend the `Shape` class to create new shape classes (e.g., `Circle`, `Rectangle`, `Triangle`) and override the `calculateArea()` method in each subclass with the specific logic for that shape. This way, you are extending the functionality of the `Shape` class without modifying its implementation.
3. Liskov Substitution Principle (LSP):
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
   In this example, we have a base class `Shape` that defines a common method `calculateArea()` for calculating the area of a shape. The Rectangle and `Square` classes inherit from `Shape` and provide their own implementations of the `area()` method.
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
4. Interface Segregation Principle (ISP):
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
5. Dependency Inversion Principle (DIP):
   Let's consider an example where we have a `Logger` class that is responsible for logging messages. Initially, the `Logger` class directly depends on a concrete implementation of a `LogWriter`:
   ```javascript
    class Logger {
        constructor() {
            this.logWriter = new FileLogWriter();
        }

        log(message) {
            this.logWriter.write(message);
        }
    }

    class FileLogWriter {
        write(message) {
        // Implementation for writing logs to a file
        }
    }
   ```
   In this design, the `Logger` class depends on the concrete `FileLogWriter` class. However, this creates a tight coupling between the `Logger` and `FileLogWriter` implementations, making it difficult to change or extend the logging functionality.
   To adhere to the Dependency Inversion Principle, we introduce an abstraction (interface or abstract class) that both `Logger` and `LogWriter` will depend on:
   ```javascript
    class Logger {
        constructor(logWriter) {
            this.logWriter = logWriter;
        }

        log(message) {
            this.logWriter.write(message);
        }
    }

    class FileLogWriter {
        write(message) {
        // Implementation for writing logs to a file
        }
    }
   ```
   In this updated design, the `Logger` class depends on the `LogWriter` abstraction instead of a specific implementation. This allows for greater flexibility and extensibility. Now, different types of log writers can be created by implementing the `LogWriter` interface and passed to the `Logger` constructor:
   ```javascript
    class ConsoleLogWriter {
        write(message) {
            // Implementation for writing logs to the console
        }
    }

    const fileLogger = new Logger(new FileLogWriter());
    fileLogger.log("This is a file log message");

    const consoleLogger = new Logger(new ConsoleLogWriter());
    consoleLogger.log("This is a console log message");
   ```
   By depending on the abstraction (`LogWriter`), the `Logger` class is decoupled from specific implementations and can work with any class that adheres to the `LogWriter` interface. This promotes flexibility, as different types of log writers can be easily introduced or replaced without modifying the `Logger` class.