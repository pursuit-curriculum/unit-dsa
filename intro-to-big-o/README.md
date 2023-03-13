# Big O

### Setting intent

> Things that are unfamiliar often seem difficult or impossible to understand. Practice patience and give yourself time.

Think back to the beginning of the course - look at early labs and lessons. They will seem much easier to understand now that you've had time to think about them and practice the concepts.

## Trivia Questions

Look at the following code:

```js
const numbers = [1, 2, 3, 4, 5];
const printItems = (arr) => {
  for (let item in arr) {
    console.log(item);
  }
};

console.log(printItems(numbers));
```

The output is:

```
0
1
2
3
4
undefined
```

Why is the last item `undefined`?

- What is the `spread operator`? When/how is it used?
- What is the `rest operator`? When/how is it used?

## Main Problem

Let's look at some code and figure out how long it takes.

Every computer has a different speed, and many conditions can affect how fast some code runs (how many other programs are running? etc.)

Instead of using time to measure how long something takes, we are going to measure by the number of steps it takes to run the code.

For example:

```js
const getLastItem = (arr) => {
  return arr[arr.length - 1];
};
```

The code inside this function runs one time. It doesn't matter if the array has 1 item, 10 items, 100 items, or 1 million items. We can represent items by the letter `n`. The code inside the function runs the same number of operations regardless of the input array size.

The time it takes to run this function is `constant`. It does not change based on the input of the array.

Another example:

```js
const printItems = (arr) => {
  for (let item in arr) {
    console.log(item);
  }
};
```

The steps in this code run `n^1` times; If `n` is 1, it loops 1 time. If `n` is 1000, it will loop 1000 times. This function demonstrates linear growth.

Try to identify how many times `n` - each of the following code examples would run:

#### 1

```js
const getMiddleItem = (arr) => {
  return arr[Math.floor(arr.length / 2)];
};
```

#### 2

```js
const printEvenNums = (limit) => {
 const evens = [];
 for (let i = 0; i <= limit; i++) {
 if (i % 2 === 0)) {
 evens.push(i);
 }
 }
 return evens;
};
```

#### 3

For a 2d array where the length of the inner and outer array is always the same

```js
const loopTheLoop = (twoDArray) => {
  for (let i = 0; i < twoDArray.length; i++) {
    for (let j = 0; j < twoDArray[i].length; j++) {
      console.log(twoDArray[i][j]);
    }
  }
};
```

#### 4

Create an `index.html` file and open it in your browser or copy/paste the JavaScript code into Chrome

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Game</title>
    <script src="app.js"></script>
  </head>
  <body>
    <p>Refresh the page to play again</p>
  </body>
</html>
```

```js
const gameVersion1 = () => {
  const limit = 100;
  let theNumber = Math.ceil(Math.random() * limit);
  let guess = prompt(`Guess a number between 1 and ${limit}`);
  let count = 0;
  guess = Number(guess);

  while (guess !== theNumber && guess !== 0) {
    console.log(guess);
    if (guess < theNumber) {
      guess = prompt(`Too low! Guess again!`);
    } else {
      guess = prompt(`Too high! Guess again!`);
    }
    guess = Number(guess);
    count++;
  }
  if (guess === 0) {
    alert(
      `You chose to quit. The number was ${theNumber}. Please play again soon!`
    );
  } else {
    alert(
      `That's right! The number was ${theNumber}. You made ${count} guesses`
    );
  }
};
```

Play this game a few times. What is your method for finding the correct number?

Try to write it down in pseudo-code.

Now try to build an answer.

Here is a naive coding solution. But it will always be the worst-case scenario - the last guess will always be the correct one. That means it would take a while if this guessing game were between 1 and 100 million.

**Note:** - Since this code guesses solutions for you, you can just run it in node, else open the dev console up in the browser. However, be sure to comment out gameVersion1.

Now that the computer is guessing and we don't need user input, we'll use `console.log` instead.

```js
const gameVersion2 = (limit = 100) => {
  let theNumber = Math.ceil(Math.random() * limit);

  let guess = 0;

  while (guess !== theNumber) {
    if (guess < theNumber) {
      console.log(`Too low! Guess again!`);
      guess++;
    } else {
      console.log(`Too high! Guess again!`);
      guess--;
    }
  }
  console.log(
    `That's right! The number was ${number}. The number of guesses was ${guess}`
  );
};
```

How close is this solution to the one you used when trying it yourself? If it matched what you tried, can you think of another way?

Try to code your approach if it isn't how you approached it.

## Lab:

### Figure Out the Big O Notation of Solutions to Some Problems You've Solved in the Past.

Go to Canvas for the assignment.

After you've completed and submitted the lab, you can continue on the next step:

### Accumulate Points on Codewars

Continue to solve assigned problems.
