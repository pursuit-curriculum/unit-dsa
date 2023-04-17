# Arrays & Callbacks

### Setting intent

> You are enough

The media focuses on being _the best_ and constantly highlights people who are _the best_. This can cause feelings and thoughts like 'If I am not going to be the best, what is the point?'

What if we applied this to cooking? What if everyone who cooks just stopped cooking because they were not the best and they believed only the best people should cook? Our world would be a much sadder and emptier place.

You don't have to be the best to make substantial positive contributions. You do have to strive to be good, thoughtful, and willing to learn from your mistakes. This will create a valuable contributor to whatever you work on and a welcome member of any team.

## Trivia Questions

- What is the first index position of an array?
- What is a primitive data type?
- Is an array a primitive data type?
- What is the difference between:
  - `for (let i = 0; i < 5; i++)`
  - `for (i = 0; i < 5; i++)`

## Find the Index in an Array

Without using the `.indexOf` array method, write your own `findIndex` function.

The function should take an array and the string or number to be found.

If the item is found, it should return the index position. If no matching item is found, it should return -1. If multiple matches exist, only the first index positions should be replaced.

For example with the following array: `findIndex(letters, 'a')` should return 0. `findIndex(letters, 2)` should return -1.

```js
const letters = [
  "a",
  "b",
  "c",
  "d",
  "e",
  "f",
  "g",
  "h",
  "i",
  "j",
  "k",
  "l",
  "m",
  "n",
  "o",
  "p",
  "q",
  "r",
  "s",
  "t",
  "u",
  "v",
  "w",
  "x",
  "y",
  "z",
  "a",
];
```

## Drills

[Practice array methods with callbacks](https://github.com/joinpursuit/array-method-drills)

## Loop the Loop

Make a function that takes one argument, a two-dimensional array, where all the arrays are the same length, and returns the greatest sum of the numbers by row and column.

```js
const arr = [
  [10, 20, 30],
  [40, 50, 60],
  [70, -80, 90],
];

greatestSum(arr); //180
```

Bonus - test for diagonal as well

### Find the Indexes of All in an Array

The same as finding the index. However, if there is more than one match, return an array of matching index positions.

## Lab

### Part 1 

[Complete these drills and submit to canvas](https://github.com/joinpursuit/m6-array-method-drills)

### Part 2  Accumulate Points on Codewars

- [Sum Mixed Array](https://www.codewars.com/kata/sum-mixed-array)
- [Gravity Flip](https://www.codewars.com/kata/5f70c883e10f9e0001c89673)
- [Array Flattener](https://www.codewars.com/kata/57ee99a16c8df7b02d00045f)
- [Descending Order](https://www.codewars.com/kata/5467e4d82edf8bbf40000155?utm_source=newsletter)
- [Wrong Planet](https://www.codewars.com/kata/515e188a311df01cba000003)
- [Zoo Patrol](https://www.codewars.com/kata/5276c18121e20900c0000235)
- [Beer Maid](https://www.codewars.com/kata/51e04f6b544cf3f6550000c1?utm_source=newsletter)
- [Snail](https://www.codewars.com/kata/521c2db8ddc89b9b7a0000c1)


### Part 3

[Self-guided lesson and lab on `.reduce()` method](https://github.com/joinpursuit/m6-array-reduce)
