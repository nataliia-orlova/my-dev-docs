### WHEN TO USE ANNOTATIONS

// !! in other cases mostly you rely on TYPE INFERENCE and don't do TYPE ANNOTATIONS !!

1. function that returns any type

```js
const json = '{"x":10, "y": 20}';
const coordinates: { x: number, y: number } = JSON.parse(json);
console.log(coordinates);
```

2. when declare and initialize variable not at the same time - not on the same line

```js
let words = ['red', 'green', 'blue'];
let foundWord: boolean;

for (let i = 0; i < words.length; i++) {
    if (words[i] === 'green') {
        foundWord = true;
    }
}
```

3. variable whoose type can not be infered correctly

```js
let numbers = [-10, 23, -44, 54];
let numberAboveZero: boolean | number = false;

for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] > 0) {
        numberAboveZero = numbers[i];
    }
}
```
