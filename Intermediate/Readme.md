## Intermediate Concepts

### Event Handling
React handles events in a similar way to DOM elements but with some syntactical differences. Here’s a simple example where clicking a button toggles its label between "ON" and "OFF" 🔄.

```jsx
const Toggle = () => {
  const [isToggleOn, setToggle] = useState(true);

  const handleClick = () => {
    setToggle(!isToggleOn);
  };

  return (
    <button onClick={handleClick}>
      {isToggleOn ? 'ON' : 'OFF'}
    </button>
  );
};

export default Toggle;
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


### Forms and Controlled Components 📝
Controlled components allow React to control the form elements. Here’s an example of a controlled input field 📄:

```jsx
const NameForm = () => {
  const [value, setValue] = useState('');

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  const handleSubmit = (event) => {
    alert('A name was submitted: ' + value);
    event.preventDefault();
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={value} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
};
```

**Explanation**:
- **Input Value**: The input value is controlled by React state.
- **onChange**: Updates the state when the input value changes.
- **onSubmit**: Alerts the input value when the form is submitted.

### Map Function
The `map()` function is used to iterate over an array and render each item. Here’s an example that renders a list of items 📋:

#### Example (Mapping on Numbers)
```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>
    {number}
  </li>
);
```

#### Example (Mapping on objects in an array)
```jsx
const users = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Doe' },
  { id: 3, name: 'Jane' }
];
const listItems = users.map((user) =>
  <li key={user.id}>
    {user.name}
  </li>
);
```

**Explanation**:
- **Mapping**: Iterates over each item in the array and returns a list of elements.

