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

## Linters

ESLint
: a favorite of many developers. ESLint is an open-source plugin for JavaScript and JSX that’s mainly used on the command line. All its rules are pluggable, so developers can create the linting rules they prefer.

Flow
: a static JavaScript code checked developed by Facebook. Flow checks your code for errors through static type annotations, but it only needs a minimum of such descriptions because it infers types and tracks data as it moves through your code.

Prettier
: an opinionated code formatter that saves you time discussing style in code reviews. Prettier integrates with most editors and supports JavaScript, HTML, CSS, GraphQL, Markdown, YAML, and more languages through community plugins.

## Literals

### Array

#### Removing an element
The better approach is to use `Array.prototype.filter()` method.

```js
arr.filter((item, i) => i !== index)
```