# Variables

## Declaration

> **Note:** while `var` has been available in JavaScript since its initial release, `let` and `const` are only available in ES6 (ES2015) and up.

You can write all of these declarations in the global context (i.e. outside of any function), but even within a function, if you forget to write `var`, `let` or `const` before an assignment, the variable will automatically be global.

### var

```js
var x; // Declaration and initialization
x = "Hello World"; // Assignment

// Or all in one
var y = "Hello World";
```

This declaration is probably the most popular, as there was no alternative until ECMAScript 6. Variables declared with `var` are available in the scope of the enclosing function. If there is no enclosing function, they are available globally.

## let

```js
let x; // Declaration and initialization
x = "Hello World"; // Assignment

// Or all in one
let y = "Hello World";
```

`let` is the descendant of `var` in modern JavaScript. Its scope is not only limited to the enclosing function, but also to its enclosing block statement. A block statement is everything inside `{` and `}`, (e.g. an if condition or loop). The benefit of `let` is it reduces the possibility of errors, as variables are only available within a smaller scope.

## const

```js
const x = "Hello World";
```

Technically a constant isn’t a variable. The particularity of a constant is that you need to assign a value when declaring it and there is no way to reassign it. A const is limited to the scope of the enclosing block, like `let`.

Constants should be used whenever a value must not change during the applications running time, as you’ll be notified by an error when trying to overwrite them.

## Cloning

### shallow copy
```js
let newDescriptions = [...this.state.descriptions]
let newDescriptions = Object.assign([], this.state.descriptions)
```

### deep copy
```js
import _ from 'lodash'

let newDescriptions = JSON.parse(JSON.stringify(this.state.descriptions))
let newDescriptions = _.cloneDeep(this.state.descriptions)
```

## Conditional Operations

```javascript
if ( value ) {}
```

will evaluate to `true` if `value` is not:

- `null`
- `undefined`
- `NaN`
- empty string (`""`)
- `0`
- `false`

The above list represents all possible `falsy` values in ECMA-/Javascript. Find it in the [specification](https://www.ecma-international.org/ecma-262/5.1/#sec-9.2) at the **ToBoolean** section.

Furthermore, if you do not know whether a variable exists (that means, if it was declared) you should check with the typeof operator. For instance

```js
if (typeof foo !== 'undefined') {
  // foo could get resolved and it is defined
}
```

If you can be sure that a variable is declared at least, you should directly check if it has a truthy value like shown above.
