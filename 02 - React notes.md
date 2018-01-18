## Notes

#### Component lifecycles

* setting state updates component - `componentDidUpdate` fires when `setState` is called
* `componentDidUpdate` fires after the DOM is updated

#### React.Children

* `React.Children` provides helper methods that let for example map over all the children without worrying if they exist or if they are a single element or an array.
* `React.Children.map(children, (child, index) => { index < 1 ? return : child })` maps over children and returns all children but the first one
* We can pass the props implicitly with `React.Children.map`:  
`React.Children.map(this.props.children, (child) => {  
  return React.cloneElement(child, {  
    propName: this.state.stateName  
  })  
})`

#### React context

* there are 3 steps to create and pass context:  
1. Telling the parent component that we are providing it with context:  
`static childContextTypes = {  
  propName: PropTypes.number.isRequired  
}`  
2. Using lifecycle hook called `getChildContext` to provide context:  
`getChildContext() {  
  return {  
    propName: this.state.stateName  
  }  
}`
3. Telling child component that we are providing it with context:  
`static contextTypes = {  
  propName: PropTypes.number.isRequired  
}`  
* now we can use the context:  
`const propName = this.context.propName`
