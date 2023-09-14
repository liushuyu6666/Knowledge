1. Optional Static Type Checking: Typescript is a statically typed language, which means the type checking is done at compile-time. The TypeScript compiler (`tsc`) will check for type mismatches at compile-time (i.e., before the code is run). However, there is a nuance, you can choose to not specify types, in which case TypeScript will use type inference to determine the types where it can. If TypeScript cannot confidently infer a type, it defaults to the `any` type, which is a flexible type that essentially bypasses the type-checking system.
2. All the numbers in TypeScript are stored as floating-point values.
3. Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compilation phase, before code execution begins. This is why it's possible to use a variable or function before it's actually declared in the code.


# Type Assertions
Type assertions are a way to tell the compiler "trust me, I know what I'm doing." It's a way to specify the type you are sure a value is of, even if TypeScript thinks it's of a different type. 

1. **Angle-bracket syntax**:
   ```typescript
    let someValue: any = "this is a string";
    let strLength: number = (<string>someValue).length;
   ```
2. **`as` syntax:**:
   ```typescript
    let someValue: any = "this is a string";
    let strLength: number = (someValue as string).length;
   ```

# Loose Equality and Strict Equality

```typescript
null == undefined  // true
null === undefined  // false
```

And we have another code snippet:
```typescript
function check(x, name) {  
    if (x == null) {  
        console.log(name + ' == null');  
    }  
    if (x === null) {  
        console.log(name + ' === null');  
    }  
    if (typeof x === 'undefined') {  
        console.log(name + ' is undefined');  
    }  
}

check(null, "test1");          // Outputs: "test1 == null" and "test1 === null"
check(undefined, "test2");     // Outputs: "test2 == null" and "test2 is undefined"
check("hello", "test3");       // Outputs nothing because none of the conditions match
```

# Convert String to Number
Use the unary operator + to convert a string to the most fitting numeric type, “3” becomes the integer 3 while “3.14” becomes the float 3.14.

```typescript
var x = "32";
var y: number = +x;
```

# Scope
1. Global Scope: defined outside of any class and can be used anywhere in the program.
2. Function/Class Scope: variables defined in a function or class can be used anywhere within that scope.
3. Local Scope/Code Block: variables defined in the local scope can be used anywhere in that block.

# Rest Parameters
Rest parameters allow you to pass a varied number of arguments (zero or more) to a function. This is useful when you’re unsure how many parameters a function will receive. All arguments after the rest symbol `...` will be stored in an array. For example:
```typescript
function Greet(greeting: string, ...names: string[]) {
    return greeting + " " + names.join(", ") + "!";
}

Greet("Hello", "Steve", "Bill"); // returns "Hello Steve, Bill!"

Greet("Hello");// returns "Hello !"
```
The rest parameter must be the last on parameter definition and you can only have 1 rest parameter per function.


# Omit & Pick Type
In TypeScript, `Omit` allows you to construct a type by picking all properties from a given type and then removing certain keys.

The general definition of `Omit` is

```typescript
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;
```

```typescript
interface FullUserInfo {
    id: number;
    name: string;
    password: string;
}

type SafeUserInfo = Omit<FullUserInfo, 'password'>;

// Equivalent to:
// type SafeUserInfo = {
//     id: number;
//     name: string;
// }

```

# interface and type
1. Extending and Implementing

2. Declaration Merging
3. Computations and Conditionals:
   * Type: Can express complex relationships and conditional types.
    ```typescript
    type Keys = 'option1' | 'option2';
    type MyMappedType = { [K in Keys]: any };
    type ConditionalType = number extends any ? string : boolean;
    ```
   * Interface: Cannot.
4. Literal Types:
   * Type: Can be used to define literal types.
    ```typescript
    type ButtonType = "submit" | "reset";
    ```
   * Interface: Cannot be used to define literal types.

# Overloading
```typescript
function add(a:string, b:string):string;

function add(a:number, b:number): number;

function add(a: any, b:any): any {
    return a + b;
}

add("Hello ", "Steve"); // returns "Hello Steve" 
add(10, 20); // returns 30 
```
1. The first two function declarations define the overloaded versions of the add function
2. The third function is the actual implementation. The actual function implementation has to be more generic (using the `any` type in this case) to handle all possible overloads. **Note**: While TypeScript has function overloading, JavaScript (which TypeScript compiles to) does not.