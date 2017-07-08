# React Notes

## Why React
* ** Front end that handles views for websites and mobile apps **
* Declarative: can describe overall result rather than describing individual steps to achieve result
* Component based: separates components to allow for reusablity
* Can be used with other frameworks

## Document Object Model
* DOM: interface for managing elements in HTML page
* Virtual DOM: JavaScript object
    * Abstraction layer between nodes in real DOM and view of code
    * Tree structure
    * Fast and cheap
    * Minimal changes when rerendering
* Three main parts:
    * Name (div, span, script)
    * Attributes: key-value pairs that add more information
    * Children (optional)
        ```
        React.createElement('Name', {
        href: "https://github.com/emptylaughter"
        , "EmptyLaughter"})
        ```

## JSX
* Optional Javascript tool that provides XML syntax
* Used for templating instead of regular JavaScript
* Looks like regular HTML
* Babel.js: Compiler that creates standard, compatible JavaScript from code that utilizes new JavaScript features and JSX
* Can use:
    * Custom attributes
    * JavaScript expressions
    * Conditional ternary expressions
        ```
        var ex = 1
        {ex == 1 ? 'It is equal to 1!' : 'It is not equal to 1!'}
        ```
* Cannot use:
    * if else statements

## The Looks (Styling, Comments, Naming)
* Inline styles: use camelCase syntax
    ```
    var theLooks = {
        fontSize: 32;
        color: '#000000'
    }

    return(
            <div>
                <h1 style = {theLooks}>So Stylish</h1>
            </div>
        )
    ```
* Comments are written with {} around them within children section of a tag
* HTML tags are written in **lowercase**
* React compoents start with **Uppercase**

## Stateless vs. Stateful Components
* Both states allow for easy maintainence because updates can be made to components without affecting everything else on the page
### Stateless
* Don't remember and cannot give context to other parts/components
* Passed as context 
    `this.props`
### Stateful
* Remembers information about app/component's state
* State can be changed
* Changes cause children/dependent components to be re-rendered

## State and Props
### State
* Mutable
* Parent (container) component should define state
* Make as simple as possible
* Have a minimal number of stateful components
### Props
* Immutable
* Children components pass data from state using props
App.jsx
```
return(
        <div>
            <h1>{this.props.headerProp}</h1>
        </div>
    );
```
main.js
```
import App from './App.jsx';

ReactDOM.render(<App headerProp = "Header from props..."/>, document.getElementById('app'));
```


## Sources
* React course: https://teamtreehouse.com
* React tutorial: https://www.tutorialspoint.com/reactjs/
* Stateful & Stateless Components: https://stackoverflow.com/questions/34512696/reactjs-difference-between-stateful-and-stateless