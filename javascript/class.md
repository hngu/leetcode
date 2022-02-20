# JavaScript Classes

## Basic class
```
export class Person {
  name;
  #id;
  
  constructor(name) {
    this.name = name;
    #id = Math.random();
  }
  
  greet() {
    console.log(`Hello my name is ${this.name}`);
  }
  
  
}
```
