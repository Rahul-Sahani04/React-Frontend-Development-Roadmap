
### Project: Todo List App

Let's create a simple Todo List app to test your knowledge! 📝

#### Step-by-Step Guide

1. **Set up the project**:
   ```bash
   npx create-react-app todo-app
   cd todo-app
   npm start
   ```

2. **Create the Todo Component**:
   Create a new file `src/Todo.js`:
   ```jsx
   import React, { useState } from 'react';
   import './Todo.css';

   function Todo() {
     const [todos, setTodos] = useState([]);
     const [newTodo, setNewTodo] = useState('');

     const addTodo = () => {
       if (newTodo.trim() !== '') {
         setTodos([...todos, newTodo]);
         setNewTodo('');
       }
     };

     const deleteTodo = (index) => {
       const updatedTodos = todos.filter((_, i) => i !== index);
       setTodos(updatedTodos);
     };

     return (
       <div className="todo-app">
         <h1>Todo List</h1>
         <input
           type="text"
           value={newTodo}
           onChange={(e) => setNewTodo(e.target.value)}
           placeholder="Add a new task..."
         />
         <button onClick={addTodo}>Add Todo</button>
         <ul>
           {todos.map((todo, index) => (
             <li key={index}>
               {todo} <button onClick={() => deleteTodo(index)}>Delete</button>
             </li>
           ))}
         </ul>
       </div>
     );
   }

   export default Todo;
   ```

3. **Style the Todo Component**:
   Create a new file `src/Todo.css`:
   ```css
   .todo-app {
     text-align: center;
     font-family: Arial, sans-serif;
     margin-top: 20px;
   }

   .todo-app input {
     padding: 10px;
     width: 200px;
     margin-right: 10px;
   }

   .todo-app button {
     padding: 10px 15px;
     cursor: pointer;
   }

   .todo-app ul {
     list-style-type: none;
     padding: 0;
   }

   .todo-app li {
     padding: 10px;
     margin: 5px 0;
     background: #f3f3f3;
     display: flex;
     justify-content: space-between;
   }
   ```

4. **Integrate Todo Component into App**:
   Update `src/App.js`:
   ```jsx
   import React from 'react';
   import './App.css';
   import Todo from './Todo';

   function App() {
     return (
       <div className="App">
         <h1>Todo List App</h1>
         <Todo />
       </div>
     );
   }

   export default App;
   ```

5. **Run the app**:
   ```bash
   npm start
   ```

   Visit `http://localhost:3000` to see your Todo List app in action.

## App Demo


<video width="100%" controls>
  <source src="todo-app/AppDemo.mp4" type="video/mp4">
</video>

### Summary

In this project, you:
- Created a stateful component to manage todos.
- Used event handling to add and delete tasks.
- Applied conditional rendering to show the list of tasks.
- Styled your app to improve the user experience.

Congratulations! 🎉 You’ve built a functional Todo List app using React’s intermediate concepts. Keep experimenting and building more complex projects!