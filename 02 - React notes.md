## Notes

#### Component lifecycles

* setting state updates component - `componentDidUpdate` fires when `setState` is called
* `componentDidUpdate` fires after the DOM is updated

#### React.Children

* `React.Children` provides helper methods that let for example map over all the children without worrying if they exist or if they are a single element or an array.
* this function maps over children and returns all children but the first one:
```jsx 
React.Children.map(children, (child, index) => { index < 1 ? return : child })
```
* We can pass the props implicitly with `React.Children.map`:  
```jsx
React.Children.map(this.props.children, (child) => {  
  return React.cloneElement(child, {  
    propName: this.state.stateName  
  })  
})
```

#### React context

There are 3 steps to create and pass context:  
1. Telling the parent component that we are providing it with context:  
```jsx
static childContextTypes = {  
  propName: PropTypes.number.isRequired  
}
```
2. Using lifecycle hook called `getChildContext` to provide context:  
```jsx
getChildContext() {  
  return {  
    propName: this.state.stateName  
  }  
}
```
3. Telling child component that we are providing it with context:  
```jsx
static contextTypes = {  
  propName: PropTypes.number.isRequired  
}
```
* now we can use the context:  
```jsx
const propName = this.context.propName
```

#### Reusability

Make your components as reusable as possible. The main idea of a compononent is to be used in multiple projects so it is a good practice to create universal naming, limit the component to manage its own data ad rather let the parent to do it.

#### Render Props

Component can return React element but it is also possible to return a function. When this function lives in state we are able to pass it via this component.

```jsx
//This is what our RenderComponent returns

render() {
  return this.props.render(this.state.data)
}
```

```jsx
//This is how we use our component

<RenderComponent render={data => {
  <h1>{data.header}</h1>
}}/>
```

#### Multiple refs

When we map some array values we can store refs of created elements in a single array.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this._nodes = new Map();
  }

  componentDidMount() {
    this.checkNodes();
  }

  componentDidUpdate() {
    this.checkNodes();
  }

  checkNodes() {
    Array.from(this._nodes.values())
      .filter(node => node != null)
      .forEach(node => {
        // do something with node
      });
  }
  render() {
    const { values } = this.props;
    return (
       <div>
         {values.map((value, i) => (
           <div key={i} ref={c => this._nodes.set(i, c)}>{value}</div>
         ))}
       </div>
    )
  }
}
```
[source](https://github.com/facebook/react/issues/1899#issuecomment-234485054)
