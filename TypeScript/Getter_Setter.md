Here is an example of using `getter` and `setter`.
```typescript
class Person {
  private _name: string;

  get name(): string {
    return this._name;
  }

  set name(value: string) {
    this._name = value;
  }
}
```


Using getters and setters provides a number of benefits:  

1. **Flexibility**:  
    `getter` and `setter` provide a way to change the internal representation of an object's state without affecting external code that uses the object's properties.  

    There is a Rectangle class that has two properties `width` and `height`:
    ```typescript
    class Rectangle {
    constructor(public width: number, public height: number) {}
    }
    ```
    To access the `width`:
    ```typescript
    const rect = new Rectangle(10, 20);
    console.log(rect.width); // 10
    ```
    Change the internal representation of the Rectangle class to store the dimensions as an object instead of separate properties:
    ```typescript
    class Rectangle {
    private dimensions = { width: 0, height: 0 };
    constructor(width: number, height: number) {
        this.dimensions.width = width;
        this.dimensions.height = height;
    }

    get width() {
        return this.dimensions.width;
    }

    set width(value: number) {
        this.dimensions.width = value;
    }

    get height() {
        return this.dimensions.height;
    }

    set height(value: number) {
        this.dimensions.height = value;
    }
    }
    ```
    Still use the same way to access to the properties `width` and `height`.

2. **Encapsulation**: 

    There is a `Person` class that has a `name` property and a `speak` method:

    ```typescript
    class Person {
    name: string;

    constructor(name: string) {
        this.name = name;
    }

    speak() {
        console.log(`Hi, my name is ${this.name}`);
    }
    }
    ```

    Change the behavior of the name property to make it read-only, so that it can only be set in the constructor and not modified afterwards.

    ```typescript
    class Person {
    private _name: string;

    constructor(name: string) {
        this._name = name;
    }

    get name() {
        return this._name;
    }

    speak() {
        console.log(`Hi, my name is ${this._name}`);
    }
    }
    ```

3. **Validation**:  
   `getter` and `setter` can help you validate input values before they are set as a property of an object. For example, you can use a `getter` and `setter` to ensure that a name property is always a non-empty string

4. **Computed properties**: 
   You can use a `getter` to dynamically calculate a property value based on other properties of the object, such as deriving a `fullName` property from separate `firstName` and `lastName` properties.