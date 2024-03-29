# Hash Tables

## Learning Objectives

- Review `hash`, `objects`, and associated vocabulary
- Gain a basic understanding of the fundamentals of hash tables

## Definitions

### Hash

Hash usually refers to a function (or the result of a function) that converts one value to another.

For example, if one were to encrypt a password, the resulting encrypted password may be called a hash. Encrypted passwords use complicated algorithms to convert a string into a complex sequence that can only be decoded with the hash function again. Hackers can only guess the password, and through brute force, they may get the correct password, especially if the number of guesses is low.

A very simple encryption is the Caesar Cipher. It shifts letters over by a certain amount.

Single letter shift

```
a => b
b => c
```

Therefore `hello, world` becomes `Ifmmp, xpsme`.

Shift by 13

```
a => n
b => o
```

This time `hello, world` becomes `Uryyb, jbeyq`.

[Try it yourself](https://cryptii.com/pipes/caesar-cipher)

[See JavaScript code example](https://github.com/trekhleb/javascript-algorithms/tree/master/src/algorithms/cryptography/caesar-cipher)

Here is something closer to what you may see if you work on authentication/password encryption in your coding. This is the result of a hashing function called [`bcrypt`](https://en.wikipedia.org/wiki/Bcrypt)

```js
const password = 'password1234';

let hashedPassword = encrypt(password);

console.log(hashedPassword);
// $2a$04$QQkIacYPfQLVbfja6sGgzuKwwp4KjMjjpfWh4G49yJbZVDucfY0XG
```

[Try it yourself](https://www.devglan.com/online-tools/bcrypt-hash-generator)

Hashing functions used in production are very complex and sophisticated. They are usually written by people who dedicate their careers to this work. We only have to know how to use them.

### Hash Table and Associated Terms

Across computing languages, there can be a different names for the same (or very similar things). For example, we learned earlier that what JavaScript coders call an `array` in Python is often referred to as a `list`.

Let's look at some more similar, yet sometimes different, terminology.

- Associative arrays: similar to JavaScript `object`, or Python `dictionary`, or `hash` in Ruby. These are made up of key-value pairs.
- JavaScript `map` - (map the data structure, not the array method) - similar to JavaScript object, with a few key details that are different (see below)
- Hash Map and Hash Table - both are pretty similar and can be interchanged sometimes when people are describing them. They are both built-in to some languages (like Java) and have performance differences depending on the code's goal.

To tie this back to JavaScript - a JavaScript object is a type of associative array. We can use JavaScript to implement hash maps/hash tables. JavaScript has a built-in `Map` object that allows one to use some special features that a regular JavaScript object does not have.

When you are in an interview or talking to others, ask clarifying questions to be sure you are talking about the same thing.

## Hash Tables

We had `O(n)` when we searched a linked list.

```js
 search(key) {
 let node = this.head;
 while (node !== null && node.data !== key) {
 node = node.next;
 }
 return node;
 }
```

When we learned about binary search trees, we could find things at `O(log n)`.

Can we find things even faster? What if we could find things in constant `O(1)` time?

Let's use an example of an English dictionary. Let's think about how we may implement three algorithms if we were doing them in the real world:

- A linked list is like starting on the first page of a bound book and going through each page until we find the word
- A binary search is like we started in the middle of a bound book, determining if our word was higher or lower in the alphabet, and then kept choosing the next middle point until we found our word
- A hash table is like if we had some wall space and could put the first page of each letter on the wall and scan them. Then, if we don't find the word on the first page, we can go to the next page behind it until we find our word.

Even though the worst-case scenario could be `O(N)` with a hash table, it usually isn't. Because it is so unusual to end up with the worst-case scenario (just one stack of pages on a wall), the average Big O calculation is used to describe it instead of the worst-case scenario.

One further detail about the analogy of the physical dictionary on the wall: Our dictionary has many more words that start with the letter `s` than the letter `x`. That means the lookup time for `s` would end up being much longer with our system. Since we want to look things up as fast as possible, we can consider that we don't have to limit ourselves to just 26 pages (one for each letter): We could possibly do 100 pages on the wall and still be able to scan them quickly `O(1)`. However, we need a more complex system to break up the dictionary. This is where we would use something like a hash function - it would help distribute the data more evenly within our 100 pages. The system would move away from purely alphabetical means to a more complicated system for distributing the data.

[Hash tables are used for things like database indexing, caches, and sets](https://en.wikipedia.org/wiki/Hash_table) - again, with where we are in our coding journey, we don't have to build out the functionality of a cache. We just need to know how and where to use the code someone else has built for us.

Bonus - [What is a cache?](https://www.businessinsider.com/what-is-cache)

## Build a Hash Table

To build a hash table, we start with an array representing our pages on the wall.

An important thing to note is that the array size in our hash table is usually pre-set. While JavaScript does not require a pre-determined size of an array for hash tables, you would still have to consider this if you were building your own.

Just like our dictionary on the wall - we don't want the number of pages on the wall to be too small or the search time would take too long. We also don't want to make it too big since, at some point, it takes up so much space we may end up with a lot of unnecessary blank space on the wall, and it no longer becomes useful.

We will build a basic hash table that uses arbitrary values for demonstration purposes.

Our very simple hash table with having one property:

- A table, which will store the data, we will limit it to 127 array positions (often referred to as `buckets` in other write-ups)
- The table will have three properties
- The index
- an array of size two that stores
- `key` and `value` pairs

We will write a very simple hash function to mock converting a string to another value.

It will take the character code of the letters, concatenate it into one long string, and then use the modulo operator to limit the values to 0 - 127.

Remember that `A` has a character code of `65`, Z has a character code of `90`. `a` has a character code of `97`, and `z` has a character code of `122`.

[Reference table](http://sticksandstones.kstrom.com/appen.html)

[Video on character codes](https://www.youtube.com/watch?v=MijmeoH9LT4)

### Getting Started

Hash table:

```js
class HashTable {
  constructor() {
    this.table = new Array(127);
  }
}
```

### Mock Hash Function

Mock hash function (remember, production code would use something far more sophisticated - however, this is to help visualize/understand the process).

```js
class HashTable {
  constructor() {
    this.table = new Array(127);
  }
  hash(key) {
    let hash = 0;
    for (let char of key) {
      hash += key.charCodeAt(char);
    }
    return hash % this.table.length;
  }
}
```

Let's test out this function.

```js
const hashTable = new HashTable();

console.log(hashTable.hash('a')); // 97
console.log(hashTable.hash('b')); // 98
console.log(hashTable.hash('z')); // 122
console.log(hashTable.hash('Zugzwang')); // 85
```

The usefulness of this hash function on its own is not helpful. Someone interacting with our hash table should not have to use this alone. Therefore, it should be a private method used only inside the hash table. In JavaScript, we cannot (yet) make a method truly private. We can still mark it as private by changing the function name to have an underscore at the start.

```js
class HashTable {
  constructor() {
    this.table = new Array(127);
  }
  _hash(key) {
    let hash = 0;
    for (let char of key) {
      hash += key.charCodeAt(char);
    }
    return hash % this.table.length;
  }
}
```

### Set a Value inside our Hash Table

Now we want to be able to set the values inside our hash table. Our key-value pairs will be stored in an array (with a length of 2), and we will loop them up by the index we created based on the key value.

Let's look at `zugzwang` - this will be the key, let's grab a definition for it `(in chess), a situation in which the obligation to make a move in one's turn is a serious, often decisive, disadvantage.`

So, we want to enter `zugzwang` as the key, the definition as the `value`, and the hashed value as the array `index`.

Let's code it:

```js
class HashTable {
  constructor() {
    this.table = new Array(127);
  }
  set(key, value) {
    const index = this._hash(key);
    this.table[index] = [key, value];
  }
}

hashTable.set(
  'zugzwang',
  `(in chess), a situation in which the obligation to make a move in one's turn is a serious, often decisive, disadvantage.`
);
```

Why did we use backticks around the definition?

Let's look at what our hash table looks like:

```js
console.log(hashTable.table);
```

```js
[
 <87 empty items>,
 [
 'zugzwang',
 "(in chess), a situation in which the obligation to make a move in one's turn is a serious, often decisive, disadvantage."
 ],
 <39 empty items>
]
```

Let's add a couple more words.

```js
hashTable.set(
  'kerfuffle',
  `a fuss, especially one caused by conflicting views.`
);

hashTable.set(
  'whipsawed',
  `subject to two difficult situations or opposing pressures at the same time.`
);

console.log(hashTable.table);
```

```js
[
 <55 empty items>,
 [
 'whipsawed',
 'subject to two difficult situations or opposing pressures at the same time.'
 ],
 <18 empty items>,
 [ 'kerfuffle', 'a fuss, especially one caused by conflicting views' ],
 <12 empty items>,
 [
 'zugzwang',
 "(in chess), a situation in which the obligation to make a move in one's turn is a serious, often decisive, disadvantage."
 ],
 <39 empty items>
]
```

The table is an array that has a lot of empty slots. This is referred to as a sparse array.

### Access Data in Hash Table

How would someone know that `zugzwang` is in position `87`? They would not know, and they would not need to know. We would write a function to get the data for them and use the hash function to do it.

```js
 get(key) {
 const target = this._hash(key);
 return this.table[target];
 }

console.log(hashTable.get('zugzwang'))
```

### Remove Data in Hash Table

Let's add the functionality to remove an item.

We are going to remove it by key. First, we will have to use the hash function to look up the index position.

We are going to replace the values with an empty array. If we have successfully removed the data, we will return a true value. If we cannot remove the data, we will return a false value.

```js
 remove(key) {
 const index = this._hash(key);
 if (this.table[index] && this.table[index].length) {
 this.table[index] = [];
 return true;
 } else {
 return false;
 }
 }
```

### Collisions

We have 127 array positions. If we are trying to store an English language dictionary in our `hashTable`, we will, at some point, run out of space/and or - based on our hashing function, end up with a word with the same index position.

**Note:** if we were to update the definition of `zugzwang`, we should be OK to use `set`.

```js
hashTable.set('zugzwang', `an updated definition`);

console.log(hashTable.get('zugzwang'));
```

Here is another word/key that will have a hash value the same as `zugzwang`:

```js
console.log(hashTable._hash('zugzwang')); // 87
console.log(hashTable._hash('watch')); // 87
```

What do we do?

There are a few ways to solve this. The one that comes up in interviews is to create a linked list (or array) so that `zugzwang` maintains its position but now also contains a pointer to the next node, which would be (in this case) `watch` and then you could retrieve the definition of watch.

Just like our dictionary on the wall, if the word is not on the first page, we would turn to the next one and then the next one until we find the page with the definition we are looking for.

In terms of code, it would look like

```js
this.table[index] = [
  ['zugzwang', 'some definition for zugzwang'],
  ['watch', 'some definition for watch']
];
```

So now we have a 2D array - the outer array contains all the values. The inner arrays always have a length of 2. The first item is the key, and the second is the value.

Coding to `get`, `set` and removing these values requires more logic. You can follow along [here](https://www.freecodecamp.org/news/javascript-hash-table-associative-array-hashing-in-js/) or [here](https://github.com/trekhleb/javascript-algorithms/tree/master/src/data-structures/hash-table)

## JavaScript Map

[JavaScript now has a built-in Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

Generally, it is OK to use a regular JavaScript object unless you have a good reason to use a `Map` object.

Notice how you get and set values is different than using a regular JavaScript object.

Here are some of the differences between `Map` and JavaScript objects

- No accidental keys (if you wanted to create a key called `toString`, which is a method on a JavaScript object, you could not do it with a regular object, you would need `Map`)
- key types - with a regular object, you can only use strings, but with `Map`, you can use numbers, functions, objects, etc.
- key order - `Map` maintains the order in which keys are entered
- size - easily determined by using the `size` property
- iterable ( can iterate like an array or string)
- is faster for inserting/deleting

## Unique Array Using Map

The pre-lesson challenge gave you links to some solutions for generating a unique array.

Regardless if your class came to a conclusion that a hash map would be the best option, let's implement one.

```js
const animals = [
  'otter',
  'dog',
  'dog',
  'dog',
  'parakeet',
  'woodchuck',
  'cat',
  'tardigrade',
  'dog',
  'cat'
];

const uniqueArray = (arr) => {
  return arr;
};

console.log(uniqueArray(animals));
```

What is our strategy? Let's return to Polya's problem-solving strategy.

1. Do we understand all the words in the problem?
1. What are we asked to show?
1. Restate the problem in your own words
1. Is there enough information for you to find a solution?
1. What is our plan?

- create an array to store the unique values
- create a map to store keys (array values)
- loop over each value in the original array
- if the key does not exist, add it to the map, and set the value of the key to true. Therefore the next instance of the value will not be added to the array.

```js
const uniqueArray = (arr) => {
  const map = new Map();
  const unique = [];
  for (let item of arr) {
    if (!map.get(item)) {
      unique.push(item);
      map.set(item, true);
    }
  }
  return unique;
};
console.log(uniqueArray(animals));
```

Thought question - could we have done this with a regular JavaScript object?

Is there any reason to have chosen a `Map` in this instance (other than for demonstration purposes)? **Hint** - what if one of the words was `length`?

When implementing a solution for a unique array, there are many options. If you end up in a technical interview and are asked to explain your design choices, this is the reasoning they are looking for (why did you use Map? Why not a regular object, what about Set?...). You don't need a perfect answer, but you should be able to explain your reasoning.

#### Bonus

- What is the Big O for our algorithm?

- Try console logging different values to learn more about `Map`.

```js
const uniqueArray = (arr) => {
  const map = new Map();
  const unique = [];
  for (let item of arr) {
    if (!map.get(item)) {
      unique.push(item);
      map.set(item, true);
    }
  }
  console.log(map);
  console.log(map['dog']);
  return unique;
};
```

## Further Reading

Strong foundations are more important than a shaky understanding of a wider breadth of topics.

Our program has been a course where we have covered a wide breadth of topics. Each module could have easily been a year long.

Before entering this program, it is possible that you did not know what a server or database was. You needed exposure to the core concepts of full-stack web development so you could know what questions to ask and what to learn next.

You have been introduced to a lot of things that you need to know about to get a junior-level position as a developer. Your learning journey is still just beginning.

Feedback from many employers is that they are not typically impressed by watching someone create `Hello, world` in multiple languages and frameworks without the ability to do more. Nor just being able 'name drop' some latest tech or name of a data structure.

Employers prefer to see someone demonstrate strong foundations within the language(s)/frameworks that they have been learning/studying.

So be sure you know and continue to review your foundations so you can keep growing in a way that will align with your career growth. It is OK to go back to old material/concepts and get stronger. Should you need to learn a new language or framework, you'll find that your foundations will help you understand new things faster and better.

- [Pursuit Module 5](https://github.com/joinpursuit/Pursuit-Core-Web/tree/master/data-structures-%26-algorithms#labs-and-lessons) - don't be afraid to start again and go through the material again. Sometimes novelty in learning is beneficial, but so is going back and spending time with the material again.

- [Pursuit Core Web](https://github.com/joinpursuit/Pursuit-Core-Web) - go back and try to update or redo the labs and projects

- [Eloquent JavaScript](https://eloquentjavascript.net) - read about JavaScript in more depth

- [Free Code Camp](https://www.freecodecamp.org)

- [DSA in JavaScript](https://github.com/trekhleb/javascript-algorithms)

Finally, the best way to learn is to code. Keep making projects. They don't have to be great. Many of your early projects will be rough. That's because you are learning. Go back to your old projects and see what you've already learned. There is no shortcut or trick to avoid writing bad code. Writing bad code is how you learn to write good or even great code.

You should have at least one showcase personal project that you are ready to show to employers: It should start very simple, look nice in terms of CSS/UX/UI, and can be quite small in scope (a single model grocery list app). Once you have built a nice version 1, you can either try a new project that is a bit more complex or continue to build on top of your current project.

In addition, you should also continue to build things that grab your interest and/or push you to lean into your discomfort with a topic. Also, try new technologies and notice the similarities and differences between the new technology and the ones you are familiar with. Applying these practices regularly are a good way for you to level up.

Happy coding!
