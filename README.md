CodeKindness Study Guide
==========

Documents specific concepts of varying IoT programming languages and strategies.

This documentation acts as a study guide more than a verbose style guide. Most information will be short 
and to the point with resource links to specific points of interest as deemed necessary.

## Docpress

Docpress generates websites from your project's basic documentation; that is, at the very least, a `README.md` file. It also supports multiple Markdown pages in `docs/`.

Under heavy development now; guides and instructions will magically appear here when we're stable.

## Usage

Still under heavy development, consider this a preview.
Requires Node v8+.
See the Getting Started guide for more details.

```sh
$ npm install -g docpress
$ echo "# My project" > README.md
$ echo "Documented by Markdown files." >> README.md
$ docpress serve

  Docpress
  starting development - ^C to exit

  350ms ✓   first build                 
      on    watching changes
      on    livereload
      on    http://localhost:3000

  Running
```
