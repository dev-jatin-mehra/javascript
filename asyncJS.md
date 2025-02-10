# Asynchronous Execution in JavaScript

## What is Asynchronous Execution?
JavaScript is single-threaded, meaning it can only execute one operation at a time. However, it uses asynchronous execution to handle tasks that take time, like network requests, timers, and file reading, without blocking the main thread.

Asynchronous execution in JavaScript is managed using:
- Callbacks
- Promises
- Async/Await
- The Event Loop

## Example 1: Using `setTimeout`
The `setTimeout` function schedules a task to run after a delay, demonstrating asynchronous behavior.

### Code Example:
```javascript
console.log("Start");
setTimeout(() => {
    console.log("Executed after 2 seconds");
}, 2000);
console.log("End");
```

### Output:
```
Start
End
Executed after 2 seconds
```

**Explanation:**
1. "Start" is logged first.
2. `setTimeout` is called, scheduling the callback to execute after 2 seconds.
3. "End" is logged immediately because `setTimeout` is non-blocking.
4. After 2 seconds, the scheduled function executes and logs "Executed after 2 seconds".

## Example 2: Fetching Data with Promises
When fetching data from an API, JavaScript doesn’t wait for the response; instead, it continues executing other tasks.

### Code Example:
```javascript
console.log("Fetching data...");
fetch("https://jsonplaceholder.typicode.com/todos/1")
    .then(response => response.json())
    .then(data => console.log("Data received:", data))
    .catch(error => console.error("Error:", error));
console.log("Other tasks can run while waiting for response");
```

### Expected Output:
```
Fetching data...
Other tasks can run while waiting for response
Data received: { userId: 1, id: 1, title: "delectus aut autem", completed: false }
```

**Explanation:**
1. "Fetching data..." is logged first.
2. `fetch` starts fetching data but does not block further execution.
3. "Other tasks can run while waiting for response" is logged.
4. When the response is received, the `.then()` callback is executed, logging the data.

---

## Additional Questions

### 1. What is a Promise and how is it different from callbacks?
A Promise in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. It is different from callbacks because it provides a more readable and maintainable way to handle asynchronous operations, avoiding "callback hell." 

Example:
```javascript
let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Success!"), 1000);
});

promise.then(result => console.log(result));
```

### 2. Why is JavaScript Single-Threaded? (with example)
JavaScript is single-threaded because it executes code in a single call stack due to its event-driven nature. It uses an event loop to handle asynchronous operations without blocking the main thread.

Example:
```javascript
console.log("Start");
setTimeout(() => console.log("Timeout callback"), 0);
console.log("End");
```
Output:
```
Start
End
Timeout callback
```
Even though `setTimeout` has 0ms delay, it runs after synchronous code due to the event loop.

### 3. Why and how is JavaScript asynchronous? (with example)
JavaScript is asynchronous because it uses the event loop to handle operations like network requests, timers, and file reading without blocking the main thread.

Example:
```javascript
console.log("Fetching data...");
fetch("https://jsonplaceholder.typicode.com/todos/1")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
console.log("Other tasks can run while waiting for response");
```
This allows JavaScript to continue executing other tasks while waiting for the fetch request to complete.

---

## Call Stack and Event Loop
### Call Stack (Diagram & Explanation)
The call stack is a data structure that keeps track of function execution in JavaScript. It follows the Last In, First Out (LIFO) principle.

Example:
```javascript
function a() {
    b();
    console.log("Inside A");
}
function b() {
    c();
    console.log("Inside B");
}
function c() {
    console.log("Inside C");
}
a();
```
#### Call Stack Execution:
1. `a()` is called → pushed onto the stack.
2. `a()` calls `b()` → `b()` is pushed onto the stack.
3. `b()` calls `c()` → `c()` is pushed onto the stack.
4. `c()` executes → logs "Inside C" → `c()` is popped.
5. `b()` continues → logs "Inside B" → `b()` is popped.
6. `a()` continues → logs "Inside A" → `a()` is popped.

### Event Loop (Diagram & Explanation)
The event loop ensures non-blocking execution by handling asynchronous operations.

#### Event Loop Process:
1. Call stack executes synchronous code.
2. Asynchronous tasks (e.g., `setTimeout`, Promises, I/O) move to the **Web APIs**.
3. Once completed, the **callback queue** or **microtask queue** moves tasks back to the call stack.
4. The event loop continuously checks and pushes completed tasks to the call stack.

Example:
```javascript
console.log("Start");
setTimeout(() => console.log("Timeout"), 0);
console.log("End");
```
Output:
```
Start
End
Timeout
```
---


