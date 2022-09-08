# Overview

## Style Guides

[Airbnb](https://github.com/airbnb/javascript)
: A mostly reasonable approach to JavaScript

[Google](https://google.github.io/styleguide/jsguide.html)
: A JavaScript source file is described as being in Google Style if and only if it adheres to the rules herein

[Idiomatic](https://github.com/rwaldron/idiomatic.js/)
: All code in any code-base should look like a single person typed it, no matter how many people contributed.

[Standard](https://github.com/standard/standard)
: JavaScript style guide, with linter & automatic code fixer. No configuration. Automatically format code. Catch style issues & programmer errors early.

[jQuery](https://contribute.jquery.org/style-guide/js/)
: The style guides here are generally known as the "jQuery Style" and are used by jQuery, jQuery UI, and jQuery Mobile.

## Literals

### Array

#### Removing an element
The better approach is to use `Array.prototype.filter()` method.

```js
arr.filter((item, i) => i !== index)
```