# React
- [Create a project](#create-a-project)
- [JSX](#jsx)
  - [Examples](#examples)
- [Component](#component)
  - [Functional components](#functional-components)
  - [Functional components using arrow functions](#functional-components-using-arrow-functions)
- [props](#props)
  - [Root Component](#root-component)
  - [Parent Component](#parent-component)
  - [Child component](#child-component)
  - [Examples](#examples-1)
- [Conditional Rendering](#conditional-rendering)
  - [\&\& Operator](#-operator)
  - [Ternary Operator](#ternary-operator)
- [State: A Component's Memory](#state-a-components-memory)
- [Hooks](#hooks)
  - [useState](#usestate)


## Create a project
Create a React project with **Vite**, which is a modern front-end build tool.
```bash
npm create vite@latest my-react-app -- --template react
```

Then run:
```bash
# move to pj directory
cd my-react-app
# install all the dependencies
npm install
# run dev server
npm run dev
```

## JSX
JSX is a syntax extension for React that enables writing components in an intuitive, HTML-like manner. Browsers cannot directly understand JSX, so it uses Babel, a JavaScript compiler, to convert JSX into standard JS code.

### Examples
HTML:
```html
<div id="root"></div>
```

JS (React):
```js
const name = "React";
const element = <h1>Hello, {name}!</h1>;
ReactDOM.render(element, document.getElementById('root'));
```
This snipets create a React element and then renders it into a DOM node with the id 'root'.

## Component
Components are a key concept in React. They are reusable UI pieces that define individual UI elements, such as buttons and forms. By combining these components, you can build the entire UI of an app.

### Functional components
Functional components can be defined as simple JS functions. They take a props object as an argument and return JSX to represent a part of the UI.

```js
// component
function Hello(props) {
    return <h1>Hello, React!</h1>;
}
// rendering
ReactDOM.render(<Hello />, document.getElementById('root'));
```
The `<Hello />` syntax instructs the React engine to instantiate the Hello component and render it on the screen.

📝 Component names should always start with capital letter.

### Functional components using arrow functions
You can define functional components more concisely using arrow functions.

```js
// component
const Hello = (props) => {
    return <h1>Hello, React!</h1>;
}
// rendering
ReactDOM.render(<Hello />, document.getElementById('root'));
```

## props
React apps are based on 'Component Tree', which is a tree structure formed by combining several components.

📝 Props are immutable, meaning that their values cannot be changed by child components.

This characteristic ensures that data flow is unidirectional, making it predictable and easy to track.

### Root Component
The root component is positioned at the very top of the component tree. This is the component that gets rendered onto the webpage by the `ReactDOM.render()`.

### Parent Component
A parent component contains one or more child components. It is responsible for passing down props, such as data and functions, to them.

### Child component
Child components receive props from their parent component, which they use to construct their own UI.

### Examples

```js
// parent.js
function ParentComponent() {
    // pass down "greeting" props to child
    return <ChildComponent greeting="Hello、React!" />;
}

// child.js
function ChildComponent(props) {
    // display the received props
    return <h1>{props.greeting}</h1>;
}

ReactDOM.render(<ParentComponent />, document.getElementById('root'));
```
## Conditional Rendering

### && Operator
```js
function Greeting({ isLoggedIn }) {
    return (
        <div>
            {isLoggedIn && <UserGreeting />}
            {!isLoggedIn && <GuestGreeting />}
        </div>
    );
}
```

### Ternary Operator
```js
function Greeting({ isLoggedIn }) {
    return (
        <div>
            {isLoggedIn ? <UserGreeting /> : <GuestGreeting />}
        </div>
    );
}
```



## State: A Component's Memory
Components need to “remember” things: the current input value, the current image, the shopping cart. In React, this kind of component-specific memory is called state.

## Hooks
In React, functions starting with “use”, is called a Hook.


### useState

useState declares a state variable that you can update directly.

```js
import { useState } from 'react';

function MyComponent() {
  const [age, setAge] = useState(42);
  const [name, setName] = useState('Taylor');
  // ...
```