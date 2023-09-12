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