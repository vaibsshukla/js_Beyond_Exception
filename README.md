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












