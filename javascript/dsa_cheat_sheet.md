# Data Structures and Algorithms Cheat Sheet

## Arrays
- create an empty array: `const arr = []`
- to create an array of size n: `const arr = new Array(n)`
- to create a 2D array:
```
const rows = 2;
const cols = 4;
const matrix = new Array(rows);
for (let i = 0; i < rows; i++) {
  matrix[i] = new Array(cols);
}
```
- iterate an array: `arr.forEach or for (const item of arr) {}`
- `Array.every(() => condition)` returns a boolean if all elements fulfill condition
- `Array.some(() =>)` like every, but at least one
- `Array.fill(value, start (optional), end (optional))`
- `Array.filter(() => )` is especially useful if you want to remove an element
- `Array.find(() => )` returns found element else undefined
- `Array.findIndex(() => )` like find, but returns index
- `Array.map(() =>)`: iterates and returns new array. This is preferred over `forEach` for functional programming
- `Array.pop()`: removes last element
- `Array.push()`: put element at the top
- `Array.reduce(() =>)`
- `Array.reverse()`
- `Array.slice()`
- `Array.sort()`
- `Array.shift()`: removes the first element
- `Array.unshift()`: adds element to the front

## Strings

## Objects

## Maps

## Sets
- Initialize empty set: `const s = new Set()`
- With list: `const s = new Set([1,2,3,4,5])`
- set size: `s.size`
- `s.add(value)`
- `s.delete(value)`
- `s.has(value)`
- iteration: `s.forEach(() =>)` or 
```
const mySet = new Set([1, 2, 3]);

for (const value of mySet) {
  console.log(value); // logs 1, 2 and 3
}
```
- clear the set: `s.clear()`
- get a list from the set: `const arr = [...mySet]`
