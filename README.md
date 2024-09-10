# "JS Beyond 'Exception'"

> A list of funny and tricky JavaScript examples

JavaScript is a great language. It has a simple syntax, large ecosystem and, what is most important, a great community.

At the same time, we all know that JavaScript is quite a funny language with tricky parts. Some of them can quickly turn our everyday job into hell, and some of them can make us laugh out loud.

# ✍🏻 Notation

**`// ->`** is used to show the result of an expression. For example:

```js
1 + 1; // -> 2
```

# 👀 Examples

## `[]` is equal `![]`

Array is equal not array:

```js
[] == ![]; // -> true
```

### 💡 Explanation:

The abstract equality operator converts both sides to numbers to compare them, and both sides become the number `0` for different reasons. Arrays are truthy, so on the right, the opposite of a truthy value is `false`, which is then coerced to `0`. On the left, however, an empty array is coerced to a number without becoming a boolean first, and empty arrays are coerced to `0`, despite being truthy.

Here is how this expression simplifies:

```js
+[] == +![];
0 == +false;
0 == 0;
true;
```

See also [`[]` is truthy, but not `true`](#-is-truthy-but-not-true).

- [**12.5.9** Logical NOT Operator (`!`)](https://www.ecma-international.org/ecma-262/#sec-logical-not-operator)
- [**7.2.15** Abstract Equality Comparison](https://262.ecma-international.org/11.0/index.html#sec-abstract-equality-comparison)

## Split a string by a space

```js
"".split(""); // -> []
// but…
"".split(" "); // -> [""]
```

Let me clarify further with more detail:

#### Case 1: ''.split('') -> []
In this case:

You are splitting an empty string ("") by an empty string ("").
The .split('') method in JavaScript usually splits a string into individual characters. However, since the string is empty, there are no characters to split, resulting in an empty array: [].
Why?

Think of it like this: if you had a non-empty string like "abc", splitting it by an empty string would give ["a", "b", "c"]. But for an empty string, there's nothing to split.
#### Case 2: ''.split(' ') -> [""]
In this case:

You are splitting an empty string ("") by a space (" ").
The .split(' ') method looks for spaces in the string to split around. Since the string is already empty, there are no spaces to split on. JavaScript, however, will still return an array with one element, which is the original empty string ([""]).
Why?

The .split(' ') operation does not find any spaces, but the original string itself (which is empty) is treated as a single element in the resulting array.

To illustrate this more clearly: if you did "hello".split(' '), you would get ["hello"] because no spaces exist in the string "hello". Similarly, in the empty string, the empty string itself is treated as the only element, so you get [""].

#### Summary:
''.split('') returns [] because there are no characters to split.
''.split(' ') returns [""] because it treats the empty string as a single element, as there are no spaces to split.


##  A stringified string

```js
JSON.stringify("production") === "production"; // -> false
```
### 💡 Explanation:
1. JSON.stringify("production") converts the string "production" into its JSON representation, which includes the quotes. So, it returns "\"production\"".
2. On the other hand, the string "production" does not include quotes.

#### Conlusion :
Therefore, the comparison is between "\"production\"" and "production", which are not equal, leading to a result of false.

##  Non-strict comparison of a number to true

```js
1 == true; // -> true
// but…
Boolean(1.1); // -> true
1.1 == true; // -> false
```
### 💡 Explanation:
In JavaScript, the Boolean() function converts a value to a boolean. Any non-zero number, including 1.1, is considered true. Therefore, the result is true.

```js
1 == true;
1 == Number(true);
1 == 1; // -> true
// but…
1.1 == true;
1.1 == Number(true);
1.1 == 1; // -> false
```












