# React Libraries

## React Router
React Router is a powerful routing library built on top of React that helps you add new screens and flows to your 
application incredibly quickly, all while keeping the URL in sync with what's being displayed on the page.

React Router is a wrapper around the `history` library which handles interaction with the browser's `window.history` with its browser and hash histories. It also provides memory history which is useful for environments that don't have global history, such as mobile app development (React Native) and unit testing with Node.

### Router
React Router v4 provides 3 `<Router>` components:

 1. `<BrowserRouter>`
 2. `<HashRouter>`
 3. `<MemoryRouter>`

The above components will create *browser*, *hash*, and *memory* history instances. React Router v4 makes the properties and methods of the `history` instance associated with your router available through the context in the `router` object.

### Switch
You have to wrap your Route's in a `<Switch>` block because `<Switch>` is unique in that it renders a route exclusively.

First you need to add `Switch` to your imports:

```javascript
import { Switch, Router, Route } from 'react-router'
```

Then define the routes within a `<Switch>` block:

```jsx harmony
<Router>
  <Switch>
    <Route {/* ... */} />
    <Route {/* ... */} />
  </Switch>
</Router>
```

### Route
A `<Switch>` renders the first child `<Route>` that matches. A `<Route>` with no `path` always matches. So you just need
to drop the `path` attribute:

```jsx harmony
<Switch>
  <Route exact path="/" component={ Home } />
  <Route path="/user" component={ User } />
  <Route component={ NotFound } />
</Switch>
```

### History
A `history` instance has two methods for navigation purpose.

1. `push()`
2. `replace()`

If you think of the history as an array of visited locations, `push()` will add a new location to the array and `replace()` will replace the current location in the array with the new one.

While navigating you can pass props to the `history` object:

```javascript
this.props.history.push({
  pathname: '/template',
  search: '?name=sudheer',
  state: { detail: response.data }
})
```

The `search` property is used to pass query params in `push()` method.

#### Navigation
There are three different ways to achieve programmatic routing/navigation within components.

 1. **Using the `withRouter()` higher-order function:**

     The `withRouter()` higher-order function will inject the history object as a prop of the component. This object provides `push()` and `replace()` methods to avoid the usage of context.

     ```jsx harmony
     import { withRouter } from 'react-router-dom' // this also works with 'react-router-native'

     const Button = withRouter(({ history }) => (
       <button
         type='button'
         onClick={() => { history.push('/new-location') }}
       >
         {'Click Me!'}
       </button>
     ))
     ```

 2. **Using `<Route>` component and render props pattern:**

     The `<Route>` component passes the same props as `withRouter()`, so you will be able to access the history methods through the history prop.

     ```jsx harmony
     import { Route } from 'react-router-dom'

     const Button = () => (
       <Route render={({ history }) => (
         <button
           type='button'
           onClick={() => { history.push('/new-location') }}
         >
           {'Click Me!'}
         </button>
       )} />
     )
     ```

 3. **Using context:**

     This option is not recommended and treated as unstable API.

     ```jsx harmony
     const Button = (props, context) => (
       <button
         type='button'
         onClick={() => {
           context.history.push('/new-location')
         }}
       >
         {'Click Me!'}
       </button>
     )

     Button.contextTypes = {
       history: React.PropTypes.shape({
         push: React.PropTypes.func.isRequired
       })
     }
     ```

#### Redirect
The `react-router` package provides `<Redirect>` component in React Router. Rendering a `<Redirect>` will navigate to a new location. Like server-side redirects, the new location will override the current location in the history stack.

 ```javascript
 import React, { Component } from 'react'
 import { Redirect } from 'react-router'

 export default class LoginComponent extends Component {
   render() {
     if (this.state.isLoggedIn === true) {
       return <Redirect to="/your/redirect/page" />
     } else {
       return <div>{'Login Please'}</div>
     }
   }
 }
 ```

### Params
The ability to parse query strings was taken out of React Router v4 because there have been user requests over the years
to support different implementations. So the decision has been given to users to choose the implementation they like. 
The recommended approach is to use the `query-string` library.

```javascript
const queryString = require('query-string');
const parsed = queryString.parse(props.location.search);
```

You can also use `URLSearchParams` if you want something native:

```javascript
const params = new URLSearchParams(props.location.search)
const foo = params.get('name')
```

You should use a *polyfill* for IE11.

## React Redux
*Redux* is a predictable state container for JavaScript apps based on the *Flux design pattern*. Redux can be used 
together with React, or with any other view library. It is tiny (about 2kB) and has no dependencies.

Redux follows three fundamental principles:

1. **Single source of truth:** The state of your whole application is stored in an object tree within a single store. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.
2. **State is read-only:** The only way to change the state is to emit an action, an object describing what happened. This ensures that neither the views nor the network callbacks will ever write directly to the state.
3. **Changes are made with pure functions:** To specify how the state tree is transformed by actions, you write reducers. Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.



You could use **Context** in your application directly and it's great for passing down data to deeply nested components
which is what it was designed for.

**Redux** is much more powerful and provides a large number of features that the *Context* API doesn't provide. Also,
React Redux uses `context` internally but it doesn't expose this fact in the public API.

### Flux
*Flux* is an *application design paradigm* used as a replacement for the more traditional MVC pattern. It is not a framework or a library but a new kind of architecture that complements React and the concept of Unidirectional Data Flow. Facebook uses this pattern internally when working with React.

The workflow between dispatcher, stores and views components with distinct inputs and outputs as follows:

![flux](https://raw.githubusercontent.com/sudheerj/reactjs-interview-questions/master/images/flux.png)

