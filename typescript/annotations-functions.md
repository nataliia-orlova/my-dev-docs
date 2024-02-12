### ALWAYS put annotation for what function returns

annotation for arguments

```js

// arrow function
const add = (a: number, b: number): number => {
return a + b;
};
// regular named function
function divide(a: number, b: number): number{
return a / b;

}
// anonymous function assigned to a variable
const multiply = function(a: number, b: number): number {
return a \* b
}
```

```js
const logger = (message: string): void => {
    console.log(message);
};

const forecast = {
    date: new Date(),
    weather: 'sunny',
};

// destructuring of this:
//const logWeather = (forecast: {date: Date, weather: string}): void => {
// console.log(forecast.date)
// console.log(forecast.weather)
// }

// destructuring and annotations go separately
const logWeather = ({
    date,
    weather,
}: {
    date: Date,
    weather: string,
}): void => {
    console.log(date);
    console.log(weather);
};

logWeather(forecast);
```
