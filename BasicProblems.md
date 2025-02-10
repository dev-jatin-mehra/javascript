```markdown
# JavaScript Practice Problems

## 1. Sum of Two Numbers
Write a function that takes two numbers and returns their sum.

### Solution:
```javascript
function sum(a, b) {
    return a + b;
}
```

## 2. Find Maximum of Three Numbers
Write a function that takes three numbers and returns the largest one.

### Solution:
```javascript
function findMax(a, b, c) {
    return Math.max(a, b, c);
}
```

## 3. Reverse a String
Write a function that reverses a given string (e.g., "hello" becomes "olleh").

### Solution:
```javascript
function reverseString(str) {
    return str.split('').reverse().join('');
}
```

## 4. Factorial Calculator
Write a function to calculate the factorial of a number (5! = 5 × 4 × 3 × 2 × 1 = 120).

### Solution:
```javascript
function factorial(n) {
    let result = 1;
    for (let i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}
```

## 5. Check for Palindrome
Write a function that checks if a given string is a palindrome (reads the same backward as forward).

### Solution:
```javascript
function isPalindrome(str) {
    const reversed = str.split('').reverse().join('');
    return str === reversed;
}
```

## 6. FizzBuzz
Write a function that prints numbers from 1 to N, but:
- For multiples of 3, print "Fizz".
- For multiples of 5, print "Buzz".
- For multiples of both 3 and 5, print "FizzBuzz".

### Solution:
```javascript
function fizzBuzz(n) {
    for (let i = 1; i <= n; i++) {
        let output = '';
        if (i % 3 === 0) output += 'Fizz';
        if (i % 5 === 0) output += 'Buzz';
        console.log(output || i);
    }
}
```

## 7. Find Vowels in a String
Write a function that returns the number of vowels in a given string (a, e, i, o, u).

### Solution:
```javascript
function countVowels(str) {
    const matches = str.match(/[aeiou]/gi);
    return matches ? matches.length : 0;
}
```

## 8. Check Prime Number
Write a function to check if a number is prime (greater than 1 with no divisors other than 1 and itself).

### Solution:
```javascript
function isPrime(num) {
    if (num <= 1) return false;
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) return false;
    }
    return true;
}
```

## 9. Fibonacci Sequence
Write a function to generate the first N numbers in the Fibonacci sequence.

### Solution:
```javascript
function fibonacci(n) {
    const sequence = [0, 1];
    for (let i = 2; i < n; i++) {
        sequence[i] = sequence[i - 1] + sequence[i - 2];
    }
    return sequence.slice(0, n);
}
```

## 10. Title Case a Sentence
Write a function that converts the first letter of each word in a sentence to uppercase and the rest to lowercase.

### Solution:
```javascript
function titleCase(str) {
    return str.toLowerCase().split(' ')
        .map(word => word.charAt(0).toUpperCase() + word.slice(1))
        .join(' ');
}
```

