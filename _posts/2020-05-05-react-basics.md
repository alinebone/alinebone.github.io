---
layout: post
categories: development english
title: React Basics
---

React is a Javascript library used to build interfaces.   
It was built on Facebook and it's largely used by companies like Apple, Airbnb, Microsoft, Payal, etc.

# React Basics

## React Developer Tools

Before starting, it's recommendable to install the **React Developer Tools**. It can be found [here](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=pt-BR).   
The extension is already enabled for regular web sites, but it's important to make it available for `file` URLs, in case you create an HTML page and simply open it in the browser. To do it, open the url `chrome://extensions/` in the browser, find the **React Developer Tools** extension and click on ***Details***, and enable the item ***Allow access to file URLs***.

## Creating elements

To start to use React, we can just create a simple HTML page and add the following scripts:

`<script src="https://unpkg.com/react@16.7.0/umd/react.development.js"></script>`   
`<script src="https://unpkg.com/react-dom@16.7.0/umd/react-dom.development.js"></script>`

Now, before the end of the `body` tag, open a `script` and add the React code:

```javascript
ReactDOM.render(
  React.createElement("p", null, "Hello World"),
  document.getElementById("root")
);
```

`ReactDOM.render` will render the following code in the DOM. The first parameter is the `.createElement` and the second is where we are going to load the content, in this case in the `<div id="root">`.    
The `.createElement` function will create the React element, the first parameter is this element is the element we want to create, the second is any attribute we want to pass, like `style`. The third one is the children. 

The final result:

```html
<!DOCTYPE html>
<html>
<head>
  <title>React</title>
  <script src="https://unpkg.com/react@16.7.0/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom@16.7.0/umd/react-dom.development.js"></script>
</head>
<body>

  <div id="root"></div>

  <script>
     ReactDOM.render(
      React.createElement("p", null, "Hello World"),
      document.getElementById("root")
    );
  </script>
</body>
</html>
```
We can also render multiple elements adding another `.createElement` as children:

```javascript
ReactDOM.render(
  React.createElement(
    "p", 
    null, 
    React.createElement(
      "li", 
      { style: { color: "red" }},
      "list item"
    )
  ),
  document.getElementById("root")
);
```
This approach, of course, is not viable in a real-life project. We would have to nest a lot of `.createElemet` to make a real page. That's where the `JSX` enters. 

But to `JSX` code run properly, we need to add another script: the *Babel* library. *Babel* makes the browser understand `JSX`:   
`<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>`
We also need to add `type="text/babel"` in the script.

Now we don't need the `.createElement` anymore. We can just add the `JSX`/`html` as the first parameter of the `.render` method:

```javascript
<script type="text/babel">
  ReactDOM.render(
    <p>Hi</p>,
    document.getElementById("root")
  );
</script>
```

`JSX` is simular, but it's not equal to `html`. We can add `Javascript` code inside `JSX` using curly braces (`{}`):

```javascript
<script type="text/babel">
  var city = "Lisbon"

  ReactDOM.render(
    <p>Hi {city}</p>,
    document.getElementById("root")
  );
</script>
```

To add a `css` class in a tag, we add the `className` attribute. Because `class` is a reserved word in `javascript`. Ie: `<p className="title">`.

## React components

A component is a piece of independent UI that can be reused in an application.   
Compenents can be create using functions or classes. An example function components is:

```jsx
const Greeting = () =>
  <div>
    <h1>Hello, stranger!</h1>
  </div>
```

Note that a `div` is wrapping the `h1`.  
It's required to wrap the content in a father element.

Another important thing is that we can embrace the function component with *parenthesis* `()` or *curly braces* `{}`.   
But if we use *curly braces*, we neeed to add the `return` key. Ie:

```jsx
const Greeting = () => {
  return <div>
    <h1>Hello, stranger!</h1>
  </div>
};
```
*We add `<Greeting/>` in the code to call this component.*

Also, React requires the component starts it name with an uppercase letter.

To use properties along with components, we use the `props` keyword. This allows us to create dynamic content.   
To pass a prop, we add in the component call the prop key and the value. Ie. `<Greeting name="Stranger"/>`.   
To retrieve it, we have to add the `props` key as the function parameter and to use it, add `props.key` inside the `jsx` using curly braces `{}`.
The result is:

```jsx
    const Greeting = (props) => 
      <div>
        <h1>Hello, {props.name}!</h1>
      </div>

    ReactDOM.render(
      <Greeting name="Stranger"/>,
      document.getElementById("root")
    );
  ```

For brevity, we can replace the `props` keyword with curly braces `{}` and call directly the property key.
```jsx
const Greeting = ({name}) => 
  <div>
    <h1>Hello, {name}!</h1>
  </div>
```

To start to make it real, we can define a root component called `App`, and play composing components: 

```jsx
    const App = () =>
    <div>
      <Greeting name="Stranger"/>
      <Greeting name="Aline"/>
      <Greeting name="Alien"/>
    </div>

    const Greeting = ({name}) =>
      <div>
        <h1>Welcome, {name}!</h1>
      </div>

    ReactDOM.render(
      <App/>,
      document.getElementById("root")
    );
```

A component class will work in the same way, but we don't need to pass the `props` parameter, the `props` object is already there, the only thing we need to do is to call `this.props.key`.   
We also need to extends `React.Component`, use the `render()` function to render the `jsx`, and **always** use the `return` key.  
To refactor the `Greeting` component to be a class component we do:

```jsx
class Greeting extends React.Component {
  render() {
    return <div>
      <h1>Welcome, {this.props.name}!</h1>
    </div>
  }
}
```

### States

State is an important part of React, it's where the magic happens.   
The `state` is an object containing data.
Every time we change a `state`, the page will reload and the content will update.

To create it, we use the `state` keyword: `state = {city: "Lisbon"}`. To change it, we have to di it with the `setState` function: `this.setState({city: "Lisbon"})`. Finally, to call it, we use `this.state.city`.   
We can use it this way only in class components.

## Events and Enhanced Rendering

Events are an important part of React development.
One important event is the `onClick`. Here's how to use it in a button element: `<button onClick={logIn}>Log in</buton>`, now the `logIn` function we are passing:

```jsx
logIn = () => {
  this.setState({ loggedIn: true })
}
```

We can also conditionally render components:

```jsx
{this.state.loggedIn ? <OneComponent> : <AnotherComponent>}
```

To render an array, we can use the `map` function: 

```jsx
  const names = ["Stranger", "Aline", "Alien"];

  names.map( name =>
    <p>name</p>
  )
```

When rendering a map or any other type of list, we need to add a `key`. To do it, we can pass the second parameter in the `map` function, which is an index: `names.map((name, index) =><p key={index}>name</p>)`.   
We can do it with an array of objects, if a `name` object has an `id`, we can call it in the `map` using `name.id`.

## Tooling

[Create React App](https://create-react-app.dev/) is a tool that will generate and set a React project for us. We have to install `npm` and `node` before using it. Then, we type `npx create-react-app name-of-my-app` in the terminal.

Inside the `package.json` we can see all the dependencies that *Create React App* installed for us, including `react`, `react-dom`, and `react-scripts` (which includes babel and webpack).   
All the components live inside the `src` folder.

`npm run build` will create a fast build to put on prod if we want to. To check in the browser, install the serve library `npm install serve`, then `serve -s build`, this will be the optimized production version.