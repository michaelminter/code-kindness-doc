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
