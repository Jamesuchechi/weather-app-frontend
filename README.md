# weather-app-frontend


Here's a simple weather app frontend using HTML, CSS, and JavaScript:

HTML (index.html)
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Weather App</h1>
    </header>
    <main>
        <form id="search-form">
            <input type="text" id="location" placeholder="Enter location">
            <button id="search-btn">Search</button>
        </form>
        <div id="weather-info">
            <h2 id="location-name"></h2>
            <p id="temperature"></p>
            <p id="description"></p>
            <img id="weather-icon" src="" alt="">
        </div>
    </main>
    <script src="script.js"></script>
</body>
</html>
```

CSS (styles.css)
```
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
}

header {
    background-color: #333;
    color: #fff;
    padding: 1rem;
    text-align: center;
}

main {
    max-width: 400px;
    margin: 2rem auto;
    padding: 1rem;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

#search-form {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
}

#location {
    width: 70%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#search-btn {
    width: 25%;
    padding: 0.5rem;
    background-color: #333;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#weather-info {
    text-align: center;
}

#location-name {
    font-size: 24px;
    margin-bottom: 0.5rem;
}

#temperature {
    font-size: 36px;
    font-weight: bold;
    margin-bottom: 0.5rem;
}

#description {
    font-size: 18px;
    color: #666;
    margin-bottom: 1rem;
}

#weather-icon {
    width: 50px;
    height: 50px;
}
```

JavaScript (script.js)
```
const searchForm = document.getElementById('search-form');
const locationInput = document.getElementById('location');
const searchBtn = document.getElementById('search-btn');
const weatherInfo = document.getElementById('weather-info');
const locationName = document.getElementById('location-name');
const temperature = document.getElementById('temperature');
const description = document.getElementById('description');
const weatherIcon = document.getElementById('weather-icon');

searchForm.addEventListener('submit', (e) => {
    e.preventDefault();
    const location = locationInput.value.trim();
    if (location) {
        getWeatherData(location);
    }
});

async function getWeatherData(location) {
    const apiKey = 'YOUR_API_KEY'; // Replace with your API key
    const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${location}&units=metric&appid=${apiKey}`;
    try {
        const response = await fetch(apiUrl);
        const data = await response.json();
        displayWeatherData(data);
    } catch (error) {
        console.error(error);
    }
}

function displayWeatherData(data) {
    locationName.textContent = data.name;
    temperature.textContent = `${data.main.temp}°C`;
    description.textContent = data.weather[0].description;
    weatherIcon.src = `https://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`;
    weatherInfo.style.display = 'block';
}
```

Note:
- You'll need to replace `YOUR_API_KEY` with your actual API key from OpenWeatherMap.
- This code uses the OpenWeatherMap API to fetch weather data.
- You can customize the design and functionality as per your requirements.

This is a basic example to get you started. You can enhance it further by adding more features, error handling, and styling.