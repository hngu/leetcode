# JavaScript Classes

## Basic class
```
export class Person {
  name;
  #id;
  address;
  
  constructor(name) {
    this.name = name;
    #id = Math.random();
  }
  
  greet() {
    console.log(`Hello my name is ${this.name}`);
  }
  
  #privateMethod() {
    console.log('private method');
  }
  
  get address() {
    return this.address;
  }
  
  setAddress(a) {
    this.address = a;
  }
}
```
