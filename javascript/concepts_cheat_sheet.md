# JavaScript Concepts

## Scope
- Global scope
- Functional scope
- Block Scope

## Hoisting
- declarations are hoisted, not initializations
- `var` variables are hoisted

## The `this` keyword
- It refers to an object and what that object refers to depends on how it is called or used.
- If an object calls its methods and the method has a `this` keyword, then it refers to the object.
- If `this` is called in a function, it refers to the function
- If `this` is called outside anything, it refers to the global object.
- `this` can be changed via apply, call and bind

## Closures
- Allows a inner function to recall variables declared in a outer function even after the outer function finishes execution.

## Prototypes and Inheritance
- Every object has a prototype object that can be used to store inherited properties
- For example - when Object B inherits from Object A, all of the inherited properties are stored in Object B's prototype
- In order to use these inherited properties, B can call an inherited property and JS will search for it in either Object B's own properties or Object B's prototype. If Object B's prototype doesn't have that invoked property but it has another prototype, JS can recursively search in there until it found it or the prototype chain leads to a null property.

## Async JS and Event Loop
- JS is a single threaded model and can do only one thing as a time.
- Async JS is like a cashier taking delivery orders. JS will take down the delivery order and have someone else make the order. While JS waits for an order to be fulfilled, it can take more delivery orders.
- When JS executes an async function like timeout, it lets the web/c++ API take care of the async task in a separate thread and when it is done, it will put the callback in the callback queue.
- when JS is done executing tasks in the call stack, it will check if there are any functions in the callback queue to execute, and if there are, it will remove a task FIFO and execute it in the call stack
- The event loop is responsible for checking if the call stack is empty and if it is, then checking if there is a pending callback in the event queue and if there is, it will push the callback into the call stack for JS to be executed.
