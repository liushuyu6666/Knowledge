There are some interesting things for Javascript, not sure how to categorize them.

# Promise
This is how I understand `Promise`.
When we create a `Promise` object in this way:
```javascript
const promise = new Promise((res, rej) => {
    if(condition) {
        res(val1);
    } else {
        rej(val2);
    }
})
```
The `promise` won't resolve or reject until either 
1. `promise()` is invoked or 
2. its resolution is explicitly requested using something like `promise.then(result => console.log(result))`.

To fully grasp the concept of Promises, there are several key points to understand:
1. A `Promise` constructor takes a function `(resolve, reject) => {}` as an argument, where `resolve` and `reject` are both callback functions.
2. The `resolve` function
   1. stores `val1` in a memory location termed as `resolvedValue`.
   2. sets the Promise's state to `fulfilled` to trigger the subsequent `then()` chains
   3. The following `then()` chain can access and use the `resolvedValue`.


# Higher-Order Function

In the [given code snippet](https://github.com/liushuyu6666/Jays_Express/blob/master/src/Database/DatabaseRepository.ts):
```javascript
private mongodbOperation(): DbOperation {
    return async (callback) => {
        const connection = await MongoClient.connect(MONGO_URI);
        try {
            const result = await callback(connection);  // line 5
            return result;
        } catch(error) {
            throw error;
        } finally {
            await connection.close();
        }
    };
}
```

The concept of a higher-order function is employed in the following ways:

1. The `mongodbOperation` function returns an anonymous function.
2. This anonymous function accepts a `callback` function as its parameter.
   * On line 5, the `callback` function is invoked as an asynchronous operation, taking `connection` as its sole argument and producing a result. As such, any provided implementation for this `callback` must adhere to this asynchronous structure, accepting the same argument and returning a similar result.


# Hoisting
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compilation phase, before code execution begins. This is why it's possible to use a variable or function before it's actually declared in the code.

However, it's important to note the distinction between variable declarations and initializations:
* Variable declarations are hoisted to the top and initialized with a value of `undefined`.
* Variable initializations (when you assign a value to a variable) are not hoisted.
* **Note**: This is not the case with `let` and `const`, they remain in a "temporal dead zone" where accessing them before declaration results in a ReferenceError.

Examples:
1. Variables:
   ```javascript
    console.log(foo); // undefined
    var foo = 5;
    console.log(foo); // 5

    console.log(bar); // ReferenceError: Cannot access 'bar' before initialization
    let bar = 5;
   ```
    In the above code, the declaration `var foo;` is hoisted to the top, but the initialization `foo = 5;` is not.
2. Functions:
   ```javascript
    console.log(bar()); // "Hello!"
    function bar() {
        return "Hello!";
    }
   ```
    Here, the entire function `bar` declaration is hoisted to the top, making it available before its actual position in the code.



# Closure
A closure is a function that has access to the parent scope's variables, even after the parent function has closed. In other words, closures allow JavaScript functions to have "private" variables. The function can access its own local variables, variables from the outer (parent) function, and global variables.

Example:

```javascript
function outerFunction() {
    let count = 0;
    return function innerFunction() {
        count++;
        return count;
    };
}

const increment = outerFunction();

console.log(increment());  // 1
console.log(increment());  // 2
```

In the above example, `innerFunction` is a closure that is returned from `outerFunction`. When we invoke `increment()`, it still has access to the `count` variable from `outerFunction`'s scope, even though `outerFunction` has already finished executing. This allows `count` to persist and be incremented with each call to `increment()`.
