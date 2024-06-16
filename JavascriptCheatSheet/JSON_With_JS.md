## JSON With Javascript

Content:
- [JSON Introduction](#json-introduction)
- [What is JSON?](#what-is-json)
- [Methods](#json-methods)
- [Syntax Rules](#json-syntax-rules)
- [Data Types](#json-data-types)
- [Example](#json-example)
- [Using Fetch API](#json-with-fetch-api)
- [Using Local Storage](#json-with-local-storage)
- [Using Axios](#json-with-axios)
- [Using React](#json-with-react)


## JSON Introduction
- JSON stands for JavaScript Object Notation.
- It is a lightweight data interchange format.
- It is language-independent and easy to read and write.
- It is easy to parse and generate data.
- It is based on JavaScript object syntax.

## What is JSON?
- It is a syntax for storing and exchanging data.
- It is text, written with JavaScript object notation.

## JSON Methods
- `JSON.stringify()` - Convert a JavaScript object into a string.
- `JSON.parse()` - Convert a JSON string into a JavaScript object.

```javascript

// JSON.stringify() - Convert a JavaScript object into a string.
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};
const personJSON = JSON.stringify(person);
console.log(personJSON); // {"name":"John","age":30,"city":"New York"}

// JSON.parse() - Convert a JSON string into a JavaScript object.
const personObject = JSON.parse(personJSON);
console.log(personObject); // { name: 'John', age: 30, city: 'New York' }
```

## JSON Syntax Rules
- Data is in name/value pairs
- Data is separated by commas
- Curly braces hold objects
- Square brackets hold arrays

## JSON Data Types
- Strings
- Numbers
- Objects
- Arrays
- Booleans
- Null

## JSON Example
```json
{
  "name": "John",
  "age": 30,
  "city": "New York",
  "isStudent": false,
  "courses": ["React", "Node.js", "MongoDB"],
  "address": {
    "street": "123 Main St",
    "zip": "10001"
  }
}
```

## JSON with Fetch API
```javascript
// Fetch JSON data from a URL
fetch('https://jsonplaceholder.typicode.com/posts')
  .then(response => response.json())
  .then(data => console.log(data));
```

## JSON with Local Storage
```javascript
// Save data to local storage
localStorage.setItem('person', JSON.stringify(person));

// Retrieve data from local storage
const person = JSON.parse(localStorage.getItem('person'));
console.log(person);
```

## JSON with Axios

- Axios is a popular promise-based HTTP client for making AJAX requests.
- It supports JSON data by default.

```bash
npm install axios
```

```javascript
// Fetch JSON data using Axios
axios.get('https://jsonplaceholder.typicode.com/posts')
  .then(response => console.log(response.data));
```


## JSON with React
```javascript
// Fetch JSON data in React
import React, { useState, useEffect } from 'react';

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(data => setData(data));
    }, []);

    return (
        <div>
            {data.map(item => (
            <div key={item.id}>{item.title}</div>
            ))}
        </div>
        );
    }

export default App;
```



<details>
<summary> JSON with Node.JS </summary>
<br/>

```javascript
// Read JSON data from a file
const fs = require('fs');
const data = fs.readFileSync('data.json');
const jsonData = JSON.parse(data);
console.log(jsonData);
```
</details>

<details>
<summary> JSON with Express </summary>
<br/>

```javascript
// Send JSON data from Express server
app.get('/api/data', (req, res) => {
  const data = {
    name: 'John',
    age: 30
  };
  res.json(data);
});
```
</details>

<details>
<summary> JSON with MongoDB </summary>
<br/>

```javascript
// Save JSON data to MongoDB
const mongoose = require('mongoose');
const personSchema = new mongoose.Schema({
  name: String,
  age: Number
});
const Person = mongoose.model('Person', personSchema);
const person = new Person({ name: 'John', age: 30 });
person.save();
```
</details>
