
## Advanced Concepts

### Hooks
Hooks allow you to use state and other React features without writing a class.
- **useState**:
  ```jsx
  import React, { useState } from 'react';

  function Example() {
    const [count, setCount] = useState(0);

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
          Click me
        </button>
      </div>
    );
  }
  ```
- **useEffect**:
  ```jsx
  import React, { useEffect, useState } from 'react';

  function Example() {
    const [count, setCount] = useState(0);

    useEffect(() => {
      document.title = `You clicked ${count} times`;
    });

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
          Click me
        </button>
      </div>
    );
  }
  ```

### Context API
Context provides a way to pass data through the component tree without passing props manually at every level.
```jsx
const MyContext = React.createContext();

function App() {
  return (
    <MyContext.Provider value="Hello from Context">
      <Toolbar />
    </MyContext.Provider>
  );
}

function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  return (
    <MyContext.Consumer>
      {value => <Button theme={value} />}
    </MyContext.Consumer>
  );
}
```

### React Router
React Router is used for navigating between different pages in a React application.
```bash
npm install react-router-dom
```
```jsx
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>

        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}
```

### State Management (Redux)
Redux is a state management library for managing and centralizing application state.
```bash
npm install redux react-redux
```
- **Store**: Holds the whole state tree of your application.
- **Reducer**: Specifies how the application's state changes in response to actions.
- **Actions**: Payloads of information that send data from your application to your Redux store.

```jsx
import { createStore } from 'redux';
import { Provider, connect } from 'react-redux';

// Actions
const increment = () => ({ type: 'INCREMENT' });
const decrement = () => ({ type: 'DECREMENT' });

// Reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
};

// Store
let store = createStore(counter);

// Component
function Counter({ value, increment, decrement }) {
  return (
    <div>
      <h1>{value}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </div>
  );
}

// Mapping state and dispatch to props
const mapStateToProps = state => ({ value: state });
const mapDispatchToProps = { increment, decrement };

const ConnectedCounter = connect(mapStateToProps, mapDispatchToProps)(Counter);

// App
function App() {
  return (
    <Provider store={store}>
      <ConnectedCounter />
    </Provider>
  );
}
```

## Building and Deploying a React App

1. **Build the App**:
   ```bash
   npm run build
   ```
   This will create an optimized production build in the `build` folder.

2. **Deploy**:
   You can deploy your React app to services like Netlify, Vercel, GitHub Pages, or any web server. For instance, deploying to GitHub Pages:
   ```bash
   npm install gh-pages --save-dev
   ```
   Add these scripts to your `package.json`:
   ```json
   "scripts": {
     "predeploy": "npm run build",
     "deploy": "gh-pages -d build"
   }
   ```
   Deploy:
   ```bash
   npm run deploy
   ```

Congratulations! You have completed the React Frontend Development Roadmap. Happy coding!