## Intermediate Concepts

### Event Handling
React handles events in a similar way to DOM elements but with some syntactical differences. Here’s a simple example where clicking a button toggles its label between "ON" and "OFF" 🔄.

```jsx
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isToggleOn: true };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}
```

**Explanation**:
- **Constructor**: Initializes the component’s state and binds the `handleClick` method.
- **handleClick**: Toggles the state between `true` and `false`.
- **Render**: Displays a button with text depending on the state.

### Lifecycle Methods
Lifecycle methods are special methods in class components that run at specific points in a component's lifecycle. Here's a basic example 🕰️:

```jsx
class LifecycleDemo extends React.Component {
  componentDidMount() {
    console.log('Component did mount');
  }

  componentDidUpdate() {
    console.log('Component did update');
  }

  componentWillUnmount() {
    console.log('Component will unmount');
  }

  render() {
    return <div>Check the console for lifecycle logs.</div>;
  }
}
```

**Explanation**:
- **componentDidMount**: Called once when the component is added to the DOM.
- **componentDidUpdate**: Called after the component’s updates are flushed to the DOM.
- **componentWillUnmount**: Called right before the component is removed from the DOM.

### Conditional Rendering
Render different components or elements based on a condition. Here’s an example of greeting users based on their login status 👥:

```jsx
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}
```

**Explanation**:
- **Greeting Component**: Checks `isLoggedIn` prop to determine which message to display.

### Lists and Keys
Rendering a list of items with unique keys helps React identify which items have changed. Here’s a basic example that renders a list of numbers 🔢:

```jsx
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>
      {number}
    </li>
  );
  return (
    <ul>{listItems}</ul>
  );
}
```

**Explanation**:
- **Key Attribute**: Assigns a unique key to each list item to help React identify changes.
