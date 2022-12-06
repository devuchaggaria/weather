# weather
It shows the weather in html css js

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Weather</title>

    <script
      src="https://kit.fontawesome.com/14d00c2bd8.js"
      crossorigin="anonymous"
    ></script>

    <style>
      @import url("https://fonts.googleapis.com/css2?family=Nunito:wght@200&display=swap");

      * {
        outline: none;
        margin: 0;
        padding: 0;
        border: none;
      }

      body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background-color: rgb(31, 31, 29);
        flex-direction: column;
        font-family: "Nunito", sans-serif;
      }

      .container {
        width: 45vw;
        background-color: rgb(255, 255, 255);
        padding: 2rem;
        border-radius: 0.6rem;
        -webkit-backdrop-filter: blur(10px);
        backdrop-filter: blur(10px);
      }
      .search {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
      .search button {
        background-color: aqua;
        border-radius: 5rem;
        padding: 1rem;
        color: white;
        cursor: pointer;
      }
      .search-some {
        color: gray;
        font-size: 2rem;
      }
      .showweater{
        width: 45vw;
        background-color: rgb(255, 255, 255);
        padding: 2rem;
        margin-top: 1rem;
        border-radius: 0.6rem;
        -webkit-backdrop-filter: blur(10px);
        backdrop-filter: blur(10px);
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="search">
        <i class="fas fa-location-dot search-some"></i>
        <input
          type="text"
          placeholder="Enter your damn location"
          id="city"
          value="Delhi"
        />
        <button id="hello">
          <i class="fas fa-magnifying-glass-location" id="search"></i>
        </button>
      </div>
    </div>
    <div id="Info" class="showweater">
      <p>Temperature: <span id="Temp"></span>&deg;C</p>
      <p>Humidity: <span id="Hum"></span>%</p>
      <p>Wind degrees: <span id="deg"></span>&deg;</p>
      <p>Wind speed: <span id="speed"></span>Km/hr</p>
      <p>Sun rise: <span id="rise"></span></p>
      <p>Sun set: <span id="set"></span></p>
    </div>
    <script>
      let weather = () => {
        const options = {
          method: "GET",
          headers: {
            "X-RapidAPI-Key":
              "1ce3623766msh8b33e313e0dbcb8p19076ejsnf6940c00c846",
            "X-RapidAPI-Host": "weather-by-api-ninjas.p.rapidapi.com",
          },
        };

        fetch(
          `https://weather-by-api-ninjas.p.rapidapi.com/v1/weather?city=${
            document.getElementById("city").value
          }`,
          options
        )
          .then((response) => response.json())
          .then((response) => {
            document.getElementById("Temp").innerHTML = response.temp;
            document.getElementById("Hum").innerHTML = response.humidity;
            document.getElementById("deg").innerHTML = response.wind_degrees;
            document.getElementById("speed").innerHTML = response.wind_speed;
            document.getElementById("rise").innerHTML = new Date(response.sunrise);
            document.getElementById("set").innerHTML = new Date(response.sunset);
            console.log(response);
          })
          .catch((err) => console.error(err));
      };
      weather();
      document.getElementById("search").addEventListener("click" , ()=>{
        weather();
      })
    </script>
  </body>
</html>

```
