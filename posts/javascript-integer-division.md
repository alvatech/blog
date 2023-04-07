---
title: Gotchas in Integer Division in JavaScript
date: 2023-04-04
---

JavaScript is a very flexible and powerful language, but it also has some quirks that can cause confusion and frustration. One of these quirks is how it handles integer division, or dividing two numbers and getting a whole number as a result.

## All Numbers are Floats

The first thing to understand is that JavaScript does not have a separate data type for integers. All numbers in JavaScript are represented as floating-point numbers, which means they can have decimal parts. For example, the number 42 is actually stored as 42.0 internally.

This means that when you use the division operator (/) to divide two numbers, you will always get a floating-point number as a result, even if both numbers are whole numbers. For example:

```javascript
var x = 10 / 2 // x is 5.0
var y = 9 / 2 // y is 4.5
```

This can be problematic if you want to perform integer division, or get the quotient of two numbers without any decimal parts. For example, if you want to find out how many times 3 goes into 13, you might expect to get 4 as an answer, but instead you will get 4.333333333333333.

## Using Math.floor

One way to perform integer division in JavaScript is to use the Math.floor method. This method rounds down a given number to the nearest integer, so if we pass a floating-point number to it, it will return the integer that is less than or equal to that number. For example:

```javascript
var x = Math.floor(10 / 2) // x is 5
var y = Math.floor(9 / 2) // y is 4
var z = Math.floor(13 / 3) // z is 4
```

This seems to work fine for positive numbers, but what about negative numbers? Let's see what happens when we try to divide -9 by 2:

```javascript
var x = Math.floor(-9 / 2) // x is -5
```

Wait a minute, that's not right! We would expect to get -4 as an answer, since -4 \* 2 = -8 and -8 + 1 = -9. But Math.floor always rounds down, so it returns -5 instead.

This is because Math.floor follows the mathematical definition of floor, which is the largest integer less than or equal to a given value. In mathematics, the floor of -4.5 is -5, as -5 is the "highest possible integral number that is still lower than -4.5.

But this is not what we want when we perform integer division. We want to get the closest integer to the quotient of two numbers, regardless of their sign. We want to truncate the decimal part of the quotient, not round it down.

## Using Math.trunc

Fortunately, there is a better way to perform integer division in JavaScript: using the Math.trunc method. This method returns the integral part of a given number, or simply removes the decimal part without rounding. For example:

```javascript
var x = Math.trunc(10 / 2) // x is 5
var y = Math.trunc(9 / 2) // y is 4
var z = Math.trunc(13 / 3) // z is 4
var w = Math.trunc(-9 / 2) // w is -4
```

As you can see, this method works correctly for both positive and negative numbers. It returns the closest integer to the quotient of two numbers, which is what we want when we perform integer division.

Math.trunc was introduced in ES6 (ECMAScript 2015), so it may not be supported by older browsers or environments. However, you can use a polyfill or a simple function to emulate its behavior:

```javascript
function trunc(x) {
  return x < 0 ? Math.ceil(x) : Math.floor(x)
}
```
