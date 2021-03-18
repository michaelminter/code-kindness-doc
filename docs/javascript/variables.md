# Variables

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
