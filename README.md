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

