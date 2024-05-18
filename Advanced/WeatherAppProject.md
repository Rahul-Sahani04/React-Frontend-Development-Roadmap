# Step-by-Step Guide: Building an Advanced React Frontend Project (Weather App)

In this guide, you'll build a complete weather application using React. This project will cover basic, intermediate, and advanced concepts, ensuring a comprehensive learning experience.

## Project Overview

### Features
- Display current weather for a given city.
- Show a 5-day weather forecast.
- Use React hooks for state management and side effects.
- Implement React Router for navigation.
- Manage state globally using Context API.
- Fetch data from an external API (OpenWeather API).
- Style components with CSS.

### Prerequisites
- Basic knowledge of JavaScript and React.
- Node.js and npm installed on your machine.

### Final Project Structure
```
weather-app/
├── public/
├── src/
│   ├── components/
│   │   ├── CurrentWeather.js
│   │   ├── Forecast.js
│   ├── context/
│   │   └── WeatherContext.js
│   ├── pages/
│   │   ├── Home.js
│   │   ├── Weather.js
│   ├── App.js
│   ├── index.js
│   ├── App.css
├── package.json
└── README.md
```

## Step 1: Set Up the Project

1. **Create a new React project:**
   ```bash
   npx create-react-app weather-app
   cd weather-app
   ```

2. **Install dependencies:**
   ```bash
   npm install axios react-router-dom
   ```

## Step 2: Create Components

1. **Create a `components` folder in `src` and add `CurrentWeather.js`:**
   ```jsx
   // src/components/CurrentWeather.js
   import React from 'react';

   function CurrentWeather({ data }) {
     if (!data) return null;

     return (
       <div>
         <h2>{data.name}</h2>
         <p>Temperature: {data.main.temp}°C</p>
         <p>Condition: {data.weather[0].description}</p>
       </div>
     );
   }

   export default CurrentWeather;
   ```

2. **Add `Forecast.js` for the 5-day forecast:**
   ```jsx
   // src/components/Forecast.js
   import React from 'react';

   function Forecast({ data }) {
     if (!data) return null;

     return (
       <div>
         <h2>5-Day Forecast</h2>
         {data.list.map((item, index) => (
           <div key={index}>
             <p>Date: {new Date(item.dt * 1000).toLocaleDateString()}</p>
             <p>Temperature: {item.main.temp}°C</p>
             <p>Condition: {item.weather[0].description}</p>
           </div>
         ))}
       </div>
     );
   }

   export default Forecast;
   ```

## Step 3: Set Up Context API for Global State

1. **Create a `context` folder in `src` and add `WeatherContext.js`:**
   ```jsx
   // src/context/WeatherContext.js
   import React, { createContext, useState, useEffect } from 'react';
   import axios from 'axios';

   const WeatherContext = createContext();

   const WeatherProvider = ({ children }) => {
     const [currentWeather, setCurrentWeather] = useState(null);
     const [forecast, setForecast] = useState(null);
     const [city, setCity] = useState('London');

     useEffect(() => {
       const fetchWeather = async () => {
         const apiKey = 'YOUR_API_KEY';
         const weatherData = await axios(
           `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`
         );
         setCurrentWeather(weatherData.data);

         const forecastData = await axios(
           `https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${apiKey}&units=metric`
         );
         setForecast(forecastData.data);
       };
       fetchWeather();
     }, [city]);

     return (
       <WeatherContext.Provider value={{ currentWeather, forecast, setCity }}>
         {children}
       </WeatherContext.Provider>
     );
   };

   export { WeatherContext, WeatherProvider };
   ```

## Step 4: Create Pages

1. **Create a `pages` folder in `src` and add `Home.js`:**
   ```jsx
   // src/pages/Home.js
   import React from 'react';

   function Home() {
     return <h2>Welcome to the Weather App</h2>;
   }

   export default Home;
   ```

2. **Add `Weather.js` to fetch and display weather data:**
   ```jsx
   // src/pages/Weather.js
   import React, { useContext } from 'react';
   import { WeatherContext } from '../context/WeatherContext';
   import CurrentWeather from '../components/CurrentWeather';
   import Forecast from '../components/Forecast';

   function Weather() {
     const { currentWeather, forecast, setCity } = useContext(WeatherContext);

     return (
       <div>
         <h2>Weather Page</h2>
         <input 
           type="text" 
           onChange={(e) => setCity(e.target.value)} 
           placeholder="Enter city" 
         />
         <CurrentWeather data={currentWeather} />
         <Forecast data={forecast} />
       </div>
     );
   }

   export default Weather;
   ```

## Step 5: Integrate React Router

1. **Update `src/App.js` to include routes:**
   ```jsx
   // src/App.js
   import React from 'react';
   import { BrowserRouter as Router, Route, Link, Switch } from 'react-router-dom';
   import Home from './pages/Home';
   import Weather from './pages/Weather';
   import { WeatherProvider } from './context/WeatherContext';
   import './App.css';

   function App() {
     return (
       <WeatherProvider>
         <Router>
           <div className="App">
             <nav>
               <ul>
                 <li><Link to="/">Home</Link></li>
                 <li><Link to="/weather">Weather</Link></li>
               </ul>
             </nav>

             <Switch>
               <Route path="/" exact component={Home} />
               <Route path="/weather" component={Weather} />
             </Switch>
           </div>
         </Router>
       </WeatherProvider>
     );
   }

   export default App;
   ```

## Step 6: Style the Application

1. **Add some basic styling to `src/App.css`:**
   ```css
   /* src/App.css */
   .App {
     text-align: center;
   }

   input {
     padding: 10px;
     margin: 20px 0;
     width: 200px;
   }

   div {
     margin-top: 20px;
   }

   nav ul {
     list-style-type: none;
     padding: 0;
   }

   nav li {
     display: inline;
     margin: 0 10px;
   }

   nav a {
     text-decoration: none;
     color: #61dafb;
   }

   nav a:hover {
     text-decoration: underline;
   }
   ```

## Step 7: Run and Test the Application

1. **Start the development server:**
   ```bash
   npm start
   ```

2. **Visit `http://localhost:3000` and navigate to the Weather page to test your weather app.**

## Challenge: Extend the Weather App

1. **Add error handling**: Show an error message if the city is not found or the API request fails.
2. **Improve styling**: Make the application more visually appealing using CSS frameworks like Bootstrap or Material-UI.
3. **Add a loading state**: Display a loading spinner while fetching data.
4. **Unit tests**: Write unit tests for your components using Jest and React Testing Library.

Congratulations! You've built an advanced React application that incorporates basic, intermediate, and advanced concepts. Happy coding! 🎉