<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather App</title>
  <style>
    body { font-family: Arial; text-align: center; margin-top: 50px; }
    #weather { margin-top: 20px; }
  </style>
</head>
<body>
  <h1>Weather App</h1>
  <input type="text" id="city" placeholder="Enter city">
  <button onclick="getWeather()">Search</button>
  <div id="weather"></div>

  <script>
    async function getWeather() {
      const city = document.getElementById('city').value;
      const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=YOUR_API_KEY&units=metric`);
      const data = await response.json();
      if(data.cod === 200) {
        document.getElementById('weather').innerHTML = `
          <h2>${data.name}</h2>
          <p>${data.weather[0].description}</p>
          <p>Temperature: ${data.main.temp} °C</p>
        `;
      } else {
        document.getElementById('weather').innerHTML = '<p>City not found!</p>';
      }
    }
  </script>
</body>
</html>
          

