# JavaScript Problems on Functions and Arrays

## Problems

1. **Function Basics**  
   Write a function `addNumbers` that takes two numbers as parameters and returns their sum.

2. **Array Traversal**  
   Write a function `printArrayElements` that takes an array and prints each element.

3. **Finding Maximum**  
   Write a function `findMax` that takes an array of numbers and returns the maximum number.

4. **Filtering Even Numbers**  
   Write a function `filterEvenNumbers` that takes an array and returns a new array containing only even numbers.

5. **Mapping to Square Values**  
   Write a function `squareArray` that takes an array of numbers and returns a new array with each number squared.

6. **Reduce to Sum**  
   Write a function `sumArray` that takes an array and returns the sum of all elements.

7. **Checking for a Value**  
   Write a function `containsValue` that takes an array and a value, and returns `true` if the value exists in the array, otherwise `false`.

8. **Reversing an Array**  
   Write a function `reverseArray` that takes an array and returns a new array with elements in reverse order.

9. **Sorting an Array in Ascending Order**  
   Write a function `sortArray` that takes an array and returns it sorted in ascending order.

10. **Counting Occurrences**  
    Write a function `countOccurrences` that takes an array and a value, and returns the number of times the value appears in the array.

---

## Solutions

1.

```js
function addNumbers(a, b) {
  return a + b;
}
```

2.

```js
function printArrayElements(arr) {
  arr.forEach((element) => console.log(element));
}
```

3.

```js
function findMax(arr) {
  return Math.max(...arr);
}
```

4.

```js
function filterEvenNumbers(arr) {
  return arr.filter((num) => num % 2 === 0);
}
```

5.

```js
function squareArray(arr) {
  return arr.map((num) => num * num);
}
```

6.

```js
function sumArray(arr) {
  return arr.reduce((sum, num) => sum + num, 0);
}
```

7.

```js
function containsValue(arr, value) {
  return arr.includes(value);
}
```

8.

```js
function reverseArray(arr) {
  return arr.slice().reverse();
}
```

9.

```js
function sortArray(arr) {
  return arr.slice().sort((a, b) => a - b);
}
```

10.

```js
function countOccurrences(arr, value) {
  return arr.reduce((count, num) => (num === value ? count + 1 : count), 0);
}
```
