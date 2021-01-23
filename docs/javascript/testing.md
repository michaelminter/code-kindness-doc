# Testing

*Jest* is a JavaScript unit testing framework created by Facebook based on Jasmine and provides automated mock creation
and a `jsdom` environment. It's often used for testing components.

There are couple of advantages compared to *Jasmine*:

- Automatically finds tests to execute in your source code.
- Automatically mocks dependencies when running your tests.
- Allows you to test asynchronous code synchronously.
- Runs your tests with a fake DOM implementation (via `jsdom`) so that your tests can be run on the command line.
- Runs tests in parallel processes so that they finish sooner.

Let's write a test for a function that adds two numbers in `sum.js` file:

 ```javascript
 const sum = (a, b) => a + b

 export default sum
 ```

 Create a file named `sum.test.js` which contains actual test:

 ```javascript
 import sum from './sum'

 test('adds 1 + 2 to equal 3', () => {
   expect(sum(1, 2)).toBe(3)
 })
 ```

 And then add the following section to your `package.json`:

 ```json
 {
   "scripts": {
     "test": "jest"
   }
 }
 ```

 Finally, run `yarn test` or `npm test` and Jest will print a result:

 ```console
 $ yarn test
 PASS ./sum.test.js
 ✓ adds 1 + 2 to equal 3 (2ms)
 ```
