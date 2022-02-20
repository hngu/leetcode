# JavaScript Classes

## Basic class
```
export class Person {
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
```
- class declarations are not hoisted
