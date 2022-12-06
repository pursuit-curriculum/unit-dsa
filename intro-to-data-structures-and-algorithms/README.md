# Intro to Data Structures & Algorithms

## Learning Objectives

By the end of this lesson, you should be able to:

- Define the term algorithm
- Define the term data structures
- Understand how you approach problem-solving
- Use Polya's problem-solving technique to solve a problem

## What are Algorithms and Data Structures?

Take a few minutes to answer for yourself either on paper or as a note to yourself in slack:

- What is an algorithm
- What is a data structure
- Have you worked with any data structures in the course so far?

Once you have your answers, compare and then take a few minutes to refine your answer:

- [intro to algorithms](https://github.com/joinpursuit/8-0-technical-curriculum/tree/main/01-fundamentals/introduction-to-algorithms)
- [data structures](https://en.wikipedia.org/wiki/Data_structure)

## Why Are We Learning about Algorithms and Data Structures

You've been working with and building algorithms throughout this course. However, you've likely been more focused on the big picture of building apps. Now we're going to focus on improving and refining your algorithm skills. This will help prepare you for technical interviews and help you improve as a developer.

This program has focused on building skills through project-based learning. When you go on a job interview, there will be other candidates who have a computer science degree (or similar), so the kinds of technical questions you receive may be geared towards CS majors. Our goal will be to introduce you to common data structures and algorithms that come up in interviews.

Technical interviews vary tremendously in what is expected. There are a few common styles, though:

- White Boarding - when you are asked to write pseudocode/flow charts/other visuals to explain your thought process in solving a problem, you may write some code snippets (i.e., for loop, if/else), but you won't be writing full code.

- Code Challenge - you are given a particular problem and asked to solve it in front of/with the people interviewing you. It is crucial to demonstrate your thought process by talking out loud/to your interviewer(s) about how you are solving the problem. It may be unimportant to solve the problem to pass - the interest can be geared towards giving you a challenging problem and seeing how you progress with it.

- Project - you are given a **small** project (build a weather app that shows today's forecast) and given some time to complete it. Then you turn it in and talk through your code with the person/people interviewing you

- Rapid Fire Trivia - this is usually over a phone screen where the interviewer asks you a bunch of trivia (is CSS case-sensitive? What is the difference between HTML and HTML5? Is JavaScript a dynamic language?).

**Note:** Be wary of projects requiring more than 1-2 days. You may be given a few days or a week, but the overall project should be small (no bigger than a module 1-4 project). Taking on projects that require a week or more of full-time++ work is not fair to your time and, anecdotally, doesn't lead to getting hired and could be taking advantage of your coding abilities.

## Emotional Framing

We are going to be giving you problems to solve. Several problems are classics like Fizz Buzz. While you can google "Fizz Buzz" and copy-paste the [exact solution](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition) you found to
"just get it done" - this will not be an acceptable strategy on a job interview. Therefore, it is better to make an earnest effort and set yourself up as if you were actually in an interview.

Also, in terms of classics, when you first start, it may seem dull or pointless to solve a problem you already have solved again. However, coding is a skill - just as an artist would not just play a song once to learn it or draw just one cat, practicing the same or similar things does help you improve. Therefore making it worthwhile to practice similar problems again and again.

You may take 40 lines of code when using Code Wars to solve a problem. When you've solved it, the answers are unlocked, and you may see a single-line solution, and your joy for solving it may fall away, and you may find yourself feeling crestfallen and wondering if you'll ever get better. You will get better! You add knowledge and skill whenever you solve a problem and analyze another solution. Speed and elegance come with practice. It's ok to go slow and have messy code at first. The only way to get better is to keep trying.

Don't get too hung up on success - each coding problem is an opportunity to learn new things. You don't need to solve the problem to have learned something. There is a high level of satisfaction in sticking through and solving a problem, but if you don't get there, take time to realize what you have learned along the way.

When you get to the actual interview process, the same principle extends. You will be challenged to learn new things. You'll be more motivated to dig into the material. You'll be asked to try to solve something you haven't solved before. Each interview is an opportunity to meet new people and learn new things. Each interview will make you stronger and better for your following interview and job.

You should try problems that you believe are "too hard" - problems that you think "I could never solve this!" Because through trying, you'll grow. If you only stick to problems that you feel are 'doable,' you will not get the same opportunity to level up. Additionally, you'll never learn the skills you need to level up and how to approach challenges that require you to grow to accomplish them.

You won't be building anything that already has a solution on the job. You are there to create solutions. So all this practice and effort is to help you get to where you can start creating solutions.

## Getting started

Beyond the main learning techniques, starting to write code is hard. You can always get started in a really simple way. Remember to work outside-in rather than left to right when building code.

Try to write the absolute least code possible that you can test. Writing many lines of code at once, without testing, can lead to many errors that feel more overwhelming to work through.

- write the function

```js
const someFunction = () => {};
```

- console log something in that function

```js
const someFunction = () => {
  console.log("hi");
};
```

- call the function

```js
someFunction;

const someFunction = () => {
  console.log("hi");
};
```

- Oops! It doesn't work. Take a moment to evaluate where you went wrong. Mistakes are normal, no matter how long you've been coding

- Talk through your mistake, understand what went wrong and correct it

```js
const someFunction = () => {
  console.log("hi");
};

someFunction;
```

- Uh oh, it still doesn't work, again evaluate why it doesn't work and try to solve it
- It's ok. Just try again

```js
const someFunction = () => {
  console.log("hi");
};

someFunction();
```

- Celebrate small victories! You figured out what was wrong and worked through it
- Try to pass a value and log that

```js
const someFunction = (name) => {
  console.log("hi", name);
};

someFunction("A.C.");
```

You have a solid start to keep building and no longer have a blank slate.
You have

- defined a function
- called the function
- passed in an argument
- confirmed that the argument is being passed in correctly.

## In Small Groups

- Discuss past interviews (from any field of work you have done)
- Bring up what makes you most anxious
- How can you work on making yourself a stronger candidate?
