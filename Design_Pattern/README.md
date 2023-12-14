- [Dependency Injection](#dependency-injection)
  - [Comparison](#comparison)
    - [Dependency Injection (DI) vs Dependency Inversion Principle (DIP)](#dependency-injection-di-vs-dependency-inversion-principle-dip)

# Dependency Injection
DI aims to achieve loose coupling between classes by injecting their dependencies from external sources, rather than having the class create its own dependencies.

Without DI:
```java
class ReportGenerator {
    private DataProvider dataProvider;

    public ReportGenerator() {
        // Creating a concrete dependency instance directly in the constructor
        this.dataProvider = new Database(); // or any other concrete class
    }

    // Other methods using dataProvider...
}
```

With DI:
```java
class ReportGenerator {
    private DataProvider dataProvider;

    public ReportGenerator(DataProvider dataProvider) {
        this.dataProvider = dataProvider;
    }

    // Other methods using dataProvider...
}
```

## Comparison
### Dependency Injection (DI) vs Dependency Inversion Principle (DIP)
Comparing with DIP code here:
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

DIP uses an abstraction however DI doesn't.