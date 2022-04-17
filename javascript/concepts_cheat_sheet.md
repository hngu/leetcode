# JavaScript Concepts

## Scope
- Global scope
- Functional scope
- Block Scope

## Hoisting
- declarations are hoisted, not initializations
- `var` variables are hoisted

## var vs let vs const
- `let` and `const` are not hoisted
- `let` and `const` are scoped within the block they are declared
- `const` cannot be used in a traditional for loop because the counter declared once and is used in the for loop scope of incrementing. `const` can be used in `for..in` or `for..of`
- `const` variables must be initialized and cannot be reassigned to something else. Also its value cannot change.

## The `this` keyword
- It refers to an object and what that object refers to depends on how it is called or used.
- If an object calls its methods and the method has a `this` keyword, then it refers to the object.
- If `this` is called in a function, it refers to the function
- If `this` is called outside anything, it refers to the global object.
- `this` can be changed via apply, call and bind

## Closures
- Allows a inner function to recall variables declared in a outer function even after the outer function finishes execution.
- Functional programming uses closures to store state while classes use "this" to attach state variables.

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


## Unicode
- JS strings should be treated as a sequence of code units, not a sequence of symbols. Each character can be represented by one or more code units.
- Use string.normalize() to normalize the string to a specific unicode normalization form.

## Dependency Injection
It provides the objects that an object needs to function, instead of having that object construct itself. Basically, pass in instances of an object to another object instead of that object creating those object instances. Very useful for testing since you can inject mocked instances
