# Weather module for Fitbit OS

This library permits to retrieve weather information from the device.  
You can choose your favourite weather provider between [Yahoo](https://query.yahooapis.com), [OpenWeatherMap](http://api.openweathermap.org), [DarkSky](https://api.darksky.net) and [WeatherUnderground](http://api.wunderground.com) [Weatherbit](https://www.weatherbit.io/)

## Installation

```javascript
npm i fitbit-weather
```

### Companion

Create an *index.js* file in the *companion* folder if you don't already have one.  
Add the following code in this file :

```javascript
import * as weather from 'fitbit-weather/companion'

weather.setup({ provider : weather.Providers.yahoo, apiKey : 'YOUR_KEY' })
```
### App

Add the following code in your *app/index.js* file

```javascript
import * as weather from 'fitbit-weather/app'

weather.fetch()
  .then(weather => console.log(JSON.stringify(weather)))
  .catch(error => console.log(JSON.stringify(error)))
```

## API

* **companion.setup({ provider, apiKey})** : configure the provider / apiKey used to fetch the weather
* **app.fetch(maximumAge = 0)** : retrieve the weather, if given the parameter is the maximum age in milliseconds of a possible cached weather data that is acceptable to return. Default is `0`

## Example of result
```json
  {
    "temperatureC":15,
    "temperatureF":59,
    "location":"Castelnau-D'Estretefonds",
    "description":"Mostly Clear",
    "isDay":false,
    "conditionCode":0,
    "realConditionCode":"this is the real conditioncode returned by the provider",
    "sunrise":1507442496594,
    "sunset":1507483356594,
    "timestamp":1507496916594
  }
```

## Condition codes
```javascript
const Conditions = {
  ClearSky        : 0,
  FewClouds       : 1,
  ScatteredClouds : 2,
  BrokenClouds    : 3,
  ShowerRain      : 4,
  Rain            : 5,
  Thunderstorm    : 6,
  Snow            : 7,
  Mist            : 8,
  Unknown         : 1000,
}
```
## Providers codes
```javascript
const Providers = {
  yahoo           : "yahoo",
  openweathermap  : "owm",
  wunderground    : "wu",
  darksky         : "darksky",
  weatherbit      : "weatherbit"
}
```

## Contribution

I'm not a javascript expert so every comment/code reactoring/best practice is appreciated. Don't hesitate to make PR and tell me what's wrong.
