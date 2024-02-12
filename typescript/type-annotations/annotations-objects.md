```js
const profile = {
    name: 'alex',
    age: 25,
    coords: {
        lat: 0,
        lng: 15,
    },
    setAge(age: number): void {
        this.age = age;
    },
};

//  destructure multiple properties
const { age }: { age: number } = profile;
const {
    coords: { lat, lng },
}: { coords: { lat: number, lng: number } } = profile;
```
