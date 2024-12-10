### **Basic JavaScript Questions**

1. **What is the difference between `var`, `let`, and `const`?**
   - Expected answer:
     - `var`: Function-scoped or globally scoped; can be redeclared and updated.
     - `let`: Block-scoped; can be updated but not redeclared in the same scope.
     - `const`: Block-scoped; cannot be updated or redeclared, and must be initialized at declaration.

2. **What is a closure in JavaScript?**
   - Expected answer: A closure is a function that retains access to variables from its lexical scope, even after the outer function has executed. Example:
     ```javascript
     function outer() {
         let counter = 0;
         return function inner() {
             counter++;
             return counter;
         };
     }
     const counterFn = outer();
     console.log(counterFn()); // 1
     console.log(counterFn()); // 2
     ```

3. **What are the differences between `null` and `undefined`?**
   - Expected answer:
     - `null`: A deliberate assignment of no value (object).
     - `undefined`: A variable that has been declared but not yet assigned a value or a function that doesn't return anything.

4. **What is the difference between `==` and `===`?**
   - Expected answer: 
     - `==` (loose equality): Compares values after type coercion.
     - `===` (strict equality): Compares both value and type, no type coercion.

5. **What is event delegation in JavaScript?**
   - Expected answer: Event delegation is a technique where you attach a single event listener to a parent element instead of multiple listeners to individual child elements. This allows handling events for dynamically added child elements.


### **Intermediate JavaScript Questions**

6. **Explain the concept of "hoisting" in JavaScript.**
   - Expected answer: Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their containing scope during compilation. However, only the declarations are hoisted, not the assignments. Example:
     ```javascript
     console.log(a); // undefined
     var a = 10;
     ```

7. **What are promises in JavaScript? How do they work?**
   - Expected answer: A promise is an object representing the eventual completion (or failure) of an asynchronous operation. Promises have three states: 
     - Pending
     - Resolved (Fulfilled)
     - Rejected
     Example:
     ```javascript
     const promise = new Promise((resolve, reject) => {
         let success = true;
         if (success) resolve('Success!');
         else reject('Failure');
     });
     promise.then(response => console.log(response)).catch(error => console.log(error));
     ```

8. **What is the `this` keyword in JavaScript, and how does it behave in different contexts?**
   - Expected answer: 
     - `this` refers to the context or the object to which a function is bound. It behaves differently in:
       - Global context: `this` refers to the global object (in browsers, `window`).
       - Object method: `this` refers to the object calling the method.
       - Event handlers: `this` refers to the element that triggered the event.
       - Arrow functions: `this` is lexically inherited from the enclosing context.

9. **What are higher-order functions in JavaScript? Can you give an example?**
   - Expected answer: A higher-order function is a function that either takes one or more functions as arguments, returns a function, or both. Example:
     ```javascript
     function greet(fn) {
         return `Hello, ${fn()}`;
     }
     function name() {
         return "John";
     }
     console.log(greet(name)); // "Hello, John"
     ```

10. **What is the purpose of `bind()`, `call()`, and `apply()` in JavaScript?**
    - Expected answer:
      - `bind()`: Returns a new function, permanently bound to the specified `this` context.
      - `call()`: Immediately invokes a function with a specified `this` context and arguments.
      - `apply()`: Similar to `call()`, but arguments are passed as an array.


### **Advanced JavaScript Questions**

11. **Explain the difference between synchronous and asynchronous execution in JavaScript.**
    - Expected answer: 
      - Synchronous execution blocks the execution of further code until the current operation completes (e.g., `alert()`, `console.log()`).
      - Asynchronous execution allows other operations to continue while waiting for the current operation to complete (e.g., `setTimeout()`, `fetch()`, Promises).

12. **What are JavaScript modules, and how do you use them?**
    - Expected answer: JavaScript modules allow you to break code into separate files, making it easier to manage dependencies and maintain code. You can use `import` and `export` to import and export functionality between files:
      ```javascript
      // in math.js
      export function add(a, b) { return a + b; }

      // in app.js
      import { add } from './math.js';
      console.log(add(2, 3));
      ```

13. **What is the event loop in JavaScript, and how does it work?**
    - Expected answer: The event loop is the mechanism that handles asynchronous callbacks in JavaScript. It continuously checks the call stack and the callback queue:
      - If the call stack is empty, the event loop moves the first callback from the queue to the call stack.
      - The event loop ensures that the execution of asynchronous code (such as promises, timeouts, and event handlers) happens after the current synchronous code.

14. **What is the difference between `Object.create()` and the `new` keyword in JavaScript?**
    - Expected answer:
      - `Object.create()`: Creates a new object with the specified prototype object and properties.
      - `new` keyword: Creates a new instance of a constructor function, sets up the prototype chain, and initializes the object with the constructor's properties and methods.

15. **What are the benefits and limitations of using JavaScript's `async`/`await` syntax?**
    - Expected answer:
      - **Benefits**:
        - Makes asynchronous code look and behave more like synchronous code.
        - Reduces callback hell and improves code readability.
      - **Limitations**:
        - `async/await` only works with promises, so if you are working with callback-based APIs, you still need to use `Promise` wrappers.
        - It can introduce performance overhead due to the implicit wrapping of asynchronous code in a promise.