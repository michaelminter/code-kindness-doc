# Properties

## Parent to Child
```js
class App extends React.Component {
  render() {    
    const listInfo = 'Something useful to ToDoList component';
    
    return (
      <ToDoList listInfoFromParent={ listInfo } />
    );
  }
}
```

## Child to Parent
Uses callback.

```js
class ToDoList extends React.Component {    
  myCallback = (dataFromChild) => {
    // Use dataFromChild here
  }
  
  render() {
    return (
      <ToDoItem callbackFromParent={ this.myCallback } />
    );
  }
}
```

Now from within ToDoItem we can pass something to callbackFromParent:
```js
class ToDoItem extends React.Component{
  someFn = () => {
    const listInfo = 'Something useful for ToDoList component';
    
    this.props.callbackFromParent(listInfo);
  }
  
  render() {
    // ...
  }
};
```

## Siblings
To pass data between siblings, you have to use the parent as an intermediary, using the steps outlined above.