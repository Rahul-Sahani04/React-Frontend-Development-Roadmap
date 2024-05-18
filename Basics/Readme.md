
## Introduction to React 🌟

React is a popular JavaScript library for building user interfaces, especially single-page applications where you need a dynamic and interactive user experience. Developed by Facebook, React allows you to build reusable UI components.

## Setting Up Your Environment ⚙️

1. **Node.js and npm**: Make sure Node.js and npm (Node Package Manager) are installed.
   - Download and install from [nodejs.org](https://nodejs.org/).

2. **Create React App**: An official tool to set up a new React project.
   ```bash
   npx create-react-app my-app
   cd my-app
   npm start
   ```
   This will create a new React application and start the development server.

> For detailed steps or notes about React projects or `create-react-app`, you can visit the [Create-React-App](/Create-React-App/Readme.md) documentation.

## Basic Concepts 📚

### JSX ✨
JSX stands for JavaScript XML. It allows you to write HTML in React.

```jsx
const element = <h1>Hello, world!</h1>;
```
<!-- ![JSX Example](https://reactjs.org/static/03ef5e52a7d8c3fffc9fca8f8b2dbece/6b2a2/getting-started.webp) -->

### Embedding Expressions in JSX
In the example below, we declare a variable called ```name``` and then use it inside JSX by wrapping it in curly braces:
```jsx
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```

### Components
Components are the building blocks of a React application. They can be functional or class-based.
- **Functional Component**:
  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }
  ```
- **Class Component**:
  ```jsx
  class Welcome extends React.Component {
    render() {
      return <h1>Hello, {this.props.name}</h1>;
    }
  }
  ```

### Props
Props (short for **"properties"**) are used to pass data from one component to another.
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return <Welcome name="Sara" />;
}
```

### State
State is used to manage data that can change over time and affect what is rendered.
```jsx
import React, { useState, useEffect } from 'react';

const Clock = () => {
  const [date, setDate] = useState(new Date());

  useEffect(() => {
    const timerID = setInterval(() => {
      setDate(new Date());
    }, 1000);

    return () => {
      clearInterval(timerID);
    };
  }, []);

  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {date.toLocaleTimeString()}.</h2>
    </div>
  );
};

export default Clock;
```


**In summary:**

- This code defines a `Clock` component that displays the current time and updates it every second.
- It uses `useState` to manage the state (current time) and `useEffect` to create a side effect (updating the time every second) with a cleanup function.
- It uses the `setInterval` function to update the time every second.

#### Output of above code.
![Clock Example](https://legacy.reactjs.org/c158617ed7cc0eac8f58330e49e48224/granular-dom-updates.gif)


7. [Counter Project](./CounterProject.md) 🔢

### Congrats! Now you can move on to the Intermediate Concepts