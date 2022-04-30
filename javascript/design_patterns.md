# Source
https://www.youtube.com/watch?v=tv-_1er1mWI

# Creational
## Singleton
- Only one instance of that object can be created
- Usually there is a `getInstance` static method to get the instance
- Good for something like a database instance. You only need one.
## Prototype
- Create clones of an instance
- Grab functionality from an existing object
- Is it different from classical inheritance by creating a flat, single hierachy called prototype chaining
- JS supports Prototype inheritance
## Builder
- Instead of requiring the consumer to create an object with the specified parameters, you can defer it
- Makes it flexible if you need to add more properties to the object and updating all the consumers to pass in another parameter
- You add functions to set the parameters later. These functions will return `this` to setup method chaining
- Hard to know if the object is really fully instantiated and you can hit NPEs in your other methods
## Factory
- Use something else to get you an instance of an object
- Factories usually create various instances of classes that are very alike. For example - a factory for creating android vs ios buttons for your React Native project. You can ask the factory and it will just return the correct button and that logic is abstracted to the factory instead of sprinkling if/else all over the code base.

# Structural
## Fascade
- Hide low level details behind an object and its methods
- a great example is jQuery. It is a fascade that hides a lot of low level JS DOM manipulation to present a set of simplified DOM APIs to use
## Proxy
- Substitute an object with another object called a proxy.
- You can use it to intercept changes to the object to trigger side effects before actually calling the original object
- Flow: client -> proxy -> original object instead of client -> original object
- JS has a Proxy object
- Use cases include: caching, access checking, additional logic checking before hitting the real object, triggering side effects

# Behavioral
## Iterator
- A way to traverse some data structure
- Classic examples include LinkedList Iterator, Tree Iterator
- will have methods like `next()` and `hasNext()`

## Observer
- An object can subscribe to events from another object
- An analogy would be that the radio control tower is the object sending events, and clients are objects receiving events
- It is a one to many relationship
- the clients subscribe to events in the radio tower and when a radio tower wants to send events, it broadcast this to all subscribers
- websockets in JS implement observer pattern

## Mediator
## State
## Strategy
