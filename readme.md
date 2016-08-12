# Introduction to ES-6

## Constants

```javascript
const PI = 3.141593;
console.log(PI);

const ATLANTA = {
  city: 'Atlanta',
  state: 'GA'
};
console.log('I live in ' + ATLANTA.city + ', ' + ATLANTA.state);

ATLANTA.city = 'Macon';
ATLANTA.zipcode = '30308';

console.log('I live in ' + ATLANTA.city + ', ' + ATLANTA.state + ' ' + ATLANTA.zipcode);
```

## Let

```javascript

function f(a, b) {
  let result;
  if (a < b) {
    result = a + b;
  }
  else {
    result = a - b;
  }
  return result;
}

console.log(f(3, 5));
console.log(f(5, 3));


function g(n) {
  let sum = 0;
  for (let i = 1; i <= n; i++) {
    sum = sum + i;
  }
  let product = 1;
  for (let i = 1; i <= n; i++) {
    product = product * i;
  }
  // console.log('the last value of i = ' + i);
  return [sum, product];
}
console.log(g(5));
```

## Arrow Functions

Arrow functions provide 2 nice advantages over older `function`s:

* Syntactic sugar - more concise thus easier to write and read
* Does not _hijack_ the `this` object


```javascript
let ages = [3, 7, 5, 12, 2];

let messages = ages.map(function(age) {
  return 'The age is ' + age;
})

console.log(messages);
```

```javascript
let ages = [3, 7, 5, 12, 2];
let messages = ages.map( age => 'The age is ' + age );
console.log(messages);
```

```javascript
let mike = {
  name: 'Mike',
  pets: [
    { name: 'Miko', age: 4 },
    { name: 'Meisha', age: 3 },
    { name: 'Deisel', age: 1 }
  ],
  averagePetAge: function() {
    let getSum = () => {
      let sum = 0;
      this.pets.forEach( (pet) => sum += pet.age );
      return sum;
    }
    return getSum() / this.pets.length;
  }
};

console.log('The average age is ' + mike.averagePetAge());
```


## Default Parameter Values

```javascript
// function sum(a, b, c) {
//  b = b || 0;
//  c = c || 0;
//  return a + b + c;
// }

function sum(a, b = 0, c = 0) {
  return a + b + c;
}

console.log(sum(1, 2, 3));
console.log(sum(1, 2));
```

## String Interpolation

```javascript
let customer = { name: "Foo" }
let card = { amount: 7, product: "Bar", unitprice: 42 }

let message =
  `  Hello ${ customer.name},
       - want to buy ${card.amount} ${card.product} for
       - a total of ${card.amount * card.unitprice} bucks?`

console.log(message);
```

## Property Shorthand

```javascript
let name = 'Mike';
let age = 29;
let pets = ['Miko', 'Meisha'];

// let person = {
//  name: name,
//     age: age,
//     pets: pets
// };

let person = { name, age, pets };

console.log(person);
```

## Classes

```javascript
// function Pet(name, age) {
//  this.name = name;
//  this.age = age;
// }
// Pet.prototype.toString = function() {
//  return `${this.name} is ${this.age} years old`;
// }

class Pet {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  toString() {
    return `${this.name} is ${this.age} years old`;
  }
  birthday() {
    this.age += 1;
  }
}

let miko = new Pet('Miko', 3);
console.log(miko.toString());
miko.birthday();
console.log(miko.toString());
```

## Resources
* [ES6 Features](http://es6-features.org)
* [ES6 Browser Compatibility Table](https://kangax.github.io/compat-table/es6/)
