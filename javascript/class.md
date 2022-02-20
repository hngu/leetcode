# JavaScript Classes

## Basic class
```
class Person {
  name;
  #id;

  static counter = 0;

  constructor(name) {
    this.name = name;
    this.#id = Math.random();
    Person.counter += 1;
  }

  greet() {
    console.log(`Hello my name is ${this.name}`);
  }

  #privateMethod() {
    console.log('private method');
  }

  get info() {
    return [this.name, this.#id];
  }

  setInfo(n, id) {
    this.name = n;
    this.#id = id;
  }

  static sameName(a, b) {
    return a.name === b.name;
  }
}
```
- class declarations are not hoisted
- constructors are not required
- instance properties can have default initialization
- private properties and fields are prepended with `#`
- can have getters and setters

## Inheritance
```
class Employee extends Person {
  company;
  
  constructor(name, company) {
    super(name);
    this.company = company;
  }
  
  greet() {
    super.greet();
    console.log(`I work at ${this.company}`);
  }
}
```
- the `super` keyword is used to access/call parent's functions
- If constructor present in subclass, must call `super()` before using `this`

## Notes
- Use to model "is-a" relationships
- Prefer composition over inheritance
- Too many subclassing can be diffult to develop/maintain
