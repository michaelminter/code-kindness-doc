# Operators

## Spread
Spread syntax `(...)` allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

## Optional Chaining
The optional chaining operator (`?.`) enables you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid.

The `?.` operator is like the `.` chaining operator, except that instead of causing an error if a reference is nullish (`null` or `undefined`), the expression short-circuits with a return value of undefined. When used with function calls, it returns `undefined` if the given function does not exist.

```js
obj.val?.prop
obj.val?.[expr]
obj.arr?.[index]
obj.func?.(args)
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining

## Nullish Coalescing Operator

It will return its right hand operand when its left hand operand is `null` or `undefined`. Otherwise it will return its left hand side operand:

```js
null ?? 'fallback';
// "fallback"

0 ?? 42;
// 0
```

## Logical OR

In JavaScript, if a certain value is falsy (like `null`, `undefined`, `0`, `''`, `NaN`), we can use the or (`||`) conditional to provide a fallback value.

```js
null ?? 'fallback';
// "fallback"

0 ?? 42;
// 42
```
