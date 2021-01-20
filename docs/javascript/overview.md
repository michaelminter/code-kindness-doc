# Overview

## Literals

### Array

#### Removing an element
The better approach is to use `Array.prototype.filter()` method.

```js
arr.filter((item, i) => i !== index)
```