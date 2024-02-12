#### Type annotations, examples:

```js
const apples: number = 5;
let speed: string = 'fast';
let hasName: boolean = true;
let nothingMuch: null = null;
let nothing: undefined = undefined;
```

build in objects

```js
let now: Date = new Date();
```

arrays

```js
// says we are going to have an array of strings or numbers
let colors: string[] = ['red', 'green', 'blue'];

let myNumbers: number[] = [1, 2, 3, 4];
```

classes

```js
class Car {}
// refering to the type of class Car
// capital - refers to the type
// lower case - refers to the instance of a Car - which is new Car()
let car: Car = new Car();
```

object literal

```js
// create an object and add type annotation to it
let point: { x: number, y: number } = {
    x: 10,
    y: 20,
};
```

functions

```js
const logNumber: (i: number) => void = (i: number) => {
    console.log(i);
};
// define what type of data goes into function as arguments
// and after => say what this function is going to return
```
