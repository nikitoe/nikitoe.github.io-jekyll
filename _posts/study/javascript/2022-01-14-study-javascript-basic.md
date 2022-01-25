---
layout: post
title: Study-JavaScript-Basic
image: /assets/img/blog/study/background-javascript.png
sitemap: false
hide_last_modified: true
categories:
  - study
  - javascript
---

# [JavaScript] 기초 이론 정리

---

* toc
{:toc .large-only}
## 1.배경_과거,현재 그리고 미래

### ✨용어

- NetScape Navigator(NetScape)
- Internet Explorer(Microsoft)
- Firefox (Moz:lla)
- Chrome(Google)
- JIT(just-in-time compilation)
- 비동기적
- 동기적
- Reverse engineering
- Ajax(Asynchronous JavaScript and XML)
- jQuery
- APIs
- ECMAScript
- SPA(Single Page Application)
- Babel
- Node.js
- TypeScript

<br>

## 2. 콘솔에 출력, script async 와 defer의 차이점 및 앞으로 자바스크립트 공부 방향 | (JavaScript ES5+)

### ✨용어

- API(Application Programming Interface)
- [MDN web docs mozilla](https://developer.mozilla.org/en-US/docs/Web/API) 👍강추
- [JavaScript 공식사이트](https://www.ecma-international.org/)
- [w3schools](https://www.w3schools.com/)
- <script></script>위치
    - head
    - head + async
    - head + defer
- `‘use strick’;` : 순수 자바스크립트를 사용할때 정의해준다.

<br>

## 3. 데이터타입, data types, let vs var, hoisting | (JavaScript ES5+)

### ✨용어

- CPU에 최적화된 연산
- 메모리의 사용을 최소화
- 입력, 연산, 출력의 중요성
- var을 사용하지 않는 이유
    - var hoisting (move declaration from bottom to top) :어디에 선언했는지와는 상관없이 항상 제일 위로 선언을 끌어 올려주는것
    - has no block scope : 블럭을 철저히 무시한다

### 👏코드 실습

#### 1.Use stricit
  - added in ES 5
  - use this for Vanila Javascript.
    
    ```jsx
    'use strict';
    ```
    
#### 2. Variable, rw (read/write)
  - let (added in ES6)
    
    ```jsx
    let name = 'nikitoe';
    console.log(name);
    name = 'hello';
    console.log(name);
    ```
    
    ```jsx
    nikitoe
    hello
    ```
    
    <br>
    
#### 3. Contant, r (read only)
  - use const whenever possible
  - only use let if variable needs to change
    
    ```jsx
    const daysInWeek = 7;
    const maxNumber = 5;
    ```
    
  - Note!!👌
    - Immutable data types: primitive types, frozen objects (i.e. object.freeze())
    - Mutable data types: all objects by default are mutable in JS
    - favor immutable data type always for a few reasons:
    - security
    - thread safety
    - reduce human mistakes
    
    <br>
    
#### 4. Variable types
  - primitive, single item: number, string, boolean, null, undefied, symbol
  - object, box container
  - function, first-class function
    
    ```jsx
    const count = 17; // integer
    const size = 17.1 // decimal number
    console.log(`value: ${count}, type: ${typeof count}`)
    console.log(`value: ${size}, type: ${typeof size}`)
    ```
    ```jsx
    value: 17, type: number
    value: 17.1, type: number
    ```
    
    <br>
    
  - number - sepcial numeric values: infinity, -infinity, NaN
    
    ```jsx
    const infinity = 1 / 0;
    const negativeInfinity = -1 / 0;
    const nAn = 'not a number' / 2;
    console.log(infinity);
    console.log(negativeInfinity);
    console.log(nAn);
    ```
    ```jsx
    Infinity
    Infinity
    NaN
    ```
    
    <br>

  - bigInt (fairly new, dont use it yet)
    
    ```jsx
    const bigInt = 123123123123123143241342353902194n; // over (-2**53~2*53)
    console.log(`value: ${bigInt}, type: ${typeof bigInt}`)
    Number.MAX_SAFE_INTEGER;
    ```
    ```jsx
    value: 123123123123123143241342353902194, type: bigint
    ```
    
    <br>
    
  -string
    
    ```jsx
    const char = 'c';
    const brendan = 'brendan';
    const greeting = 'hello' + brendan;
    console.log(`value: ${greeting}, type: ${typeof greeting}`);
    const helloBob = `hi ${brendan}!` // template literals (string)
    console.log(`value: ${helloBob}, type: ${typeof helloBob}`);
    ```
    ```jsx
    value: hellobrendan, type: string
    value: hi brendan!, type: string
    ```
    
    <br>
    
  - boolean
        - false: 0, null, undefined, NaN, ‘’
        - true: any other value
    
    ```jsx
    const canRead = true;
    const test = 3 < 1; // false
    console.log(`value: ${canRead}, type: ${typeof canRead}`)
    console.log(`value: ${test}, type: ${typeof test}`)
    ```
    ```jsx
    value: true, type: boolean
    variable.js:71 value: false, type: boolean
    ```
    
    <br>
    
  - null
    
    ```jsx
    let nothing = null;
    console.log(`value: ${nothing}, type: ${typeof nothing}`);
    ```
    ```jsx
    value: null, type: object
    ```
    
    <br>
    
  - undefined
    
    ```jsx
    let x;
    console.log(`value: ${x}, type: ${typeof x}`);
    ```
    ```jsx
    value: undefined, type: undefined
    ```
    
    <br>
    
  - symbol, create unique identifiers for objects
    
    ```jsx
    const symbol1 = Symbol('id');
    const symbol2 = Symbol('id');
    console.log(symbol1 === symbol2); // 
    const gSymbol1 = Symbol.for('id');
    const gSymbol2 = Symbol.for('id');
    console.log(gSymbol1 === gSymbol2); // true
    console.log(`value: ${symbol1.description}, type: ${typeof symbol1}`); // string으로 변환해서(description) 사용해야 에러가 발생하지 않는다.
    ```
    ```jsx
    false
    true
    value: id, type: symbol
    ```
    
    <br>
    
  - object, real-life object, data structure
    
    ```jsx
    const nikite = { name: 'nikite', age: 20 };
    ```
    
#### 5. Dynamic typing: dynamically typed language
  ```jsx
  let text = 'hello';
  console.log(text.charAt(0))
  console.log(`value: ${text}, type: ${typeof text}`);
  text = 1;
  console.log(`value: ${text}, type: ${typeof text}`);
  text = '7' + 5;
  console.log(`value: ${text}, type: ${typeof text}`);
  text = '8' / '2';
  console.log(`value: ${text}, type: ${typeof text}`);
  ```
  ```jsx
  h
  value: hello, type: string
  value: 1, type: number
  value: 75, type: string
  value: 4, type: number
  ```
<br>

## 4. 코딩의 기본 operator, if, for loop 코드리뷰 팁 | (JavaScript ES6)

### ✨용어

<br>

### 👏코드 실습

- object-oriendted programming
- class : templawte
- object : instance of a class
- JavaScript classes
- introduced in ES6
- syntactical sugar over prototype-based inheritance

#### 1. Increment and decrement operators

```jsx
let counter = 2;
const preIncrement = ++counter;
// counter = counter + 1;
// preIncrement = counter;
console.log(`preIncrement: ${preIncrement}, counter: ${counter}`);
const postIncrement = counter++;
// postIncrement = counter;
// counter = counter + 1;
console.log(`preIncrement: ${preIncrement}, counter: ${counter}`);
```

```jsx
preIncrement: 3, counter: 3
preIncrement: 3, counter: 4
```

<br>

#### 2. Assignment operators

```jsx
let x = 3;
let y = 6;
x += y; // x= x + y;
x -= y;
x *= y;
x / + y;
```

<br>

#### 3. Logical operators: || (or), && (and), ~ (not)

```jsx
//|| (or), finds the first truthy value
console.log(`or: ${value1 || value2 || check()}`);

// && (and), finds the first falsy value
console.log(`or: ${value1 && value2 && check()}`);
```

```jsx
or: true
and: false
```

<br>

#### 4. Equality

```jsx
const stringFive = '5';
const numberFive = 5;
// == loose equality, with type conversion
console.log(stringFive == numberFive);// true
console.log(stringFive != numberFive);// false

// === strict equality, no type conversion
console.log(stringFive === numberFive);// false
console.log(stringFive !== numberFive);// true
```

```jsx
true
false
false
true
```

```jsx
// object equality by reference
const nikitoe1 = { name: 'nikitoe' }
const nikitoe2= { name: 'nikitoe' }
const nikitoe= nikitoe1;
console.log(nikitoe1 == nikitoe2);// false
console.log(nikitoe1 === nikitoe2);// false
console.log(nikitoe1 === nikitoe3);// true
```

```jsx
false
false
true
```

```jsx
// equaliy - puzzler
console.log(0 == false);// true
console.log(0 === false);// false
console.log('' == false);// true
console.log('' === false);// false
console.log(null == undefined);// true
console.log(null === undefined);// false
```

```jsx
true
false
true
false
true
false
```

<br>

#### 5. Conditional operators: if

```jsx
// if, else if, else
const nickname = 'nikitoe';
if (nickname === 'nikitoe') {
    console.log('Welcome, nikitoe!');
} else if (nickname === 'coder') {
    console.log('You are amazing coder');
} else {
    console.log('unknown');
}
```

```jsx
Welcome, nikitoe!
```

<br>

#### 6. Ternary operatoer: ?

- condition ? value1 : value2;

```jsx
console.log(nickname === 'nikitoe' ? 'yes' : 'no')
```

```jsx
yes
```

<br>

#### 7. Switch statement

- use for multiple if checks
- use for enum-like value check
- use for multiple type checks in TS

```jsx
const browser = 'aa';
switch (browser) {
    case 'IE':
        console.log('go away!');
        break;
    case 'Chrome':
    case 'Firefox':
        console.log('love you!');
        break;
    default:
        console.log('same all!');
        break;
}
```

```jsx
same all!
```

<br>

#### 8. Loops

- while loop, while the condition is truthy,
- body code is executed.

```jsx
do {
    console.log(`do while: ${i}`)
    i--;
} while (i > 0);

// for loop, for(begin; condition; step)
for (i = 3; i > 0; i--) {
    console.log(`for: ${i}`);
}

for (let i = 3; i > 0; i = i - 2) {
    // inline variable declaration
    console.log(`inline variable for: ${i}`);
}
```

```jsx
while: 3
while: 2
while: 1
do while: 0
for: 3
for: 2
for: 1
inline variable for: 3
inline variable for: 1
```

<br>

- break, continue

```jsx
// Q1. iterate from 0 to 10 and print only even numbers (use continue)
for (let i = 0; i < 11; i++) {
    if (i % 2 !== 0) {
        continue;
    }
    console.log(`q1.${i}`);
}
```

```jsx
q1.0
q1.2
q1.4
q1.6
q1.8
q1.10
```

<br>

```jsx
//Q2. iterate form 0 to 10 and print numbers until reaching 8 (use break)
for (let i = 0; i < 11; i++) {
    if (i > 8) {
        break;
    }
    console.log(`q2.${i}`)
}
```

```jsx
q2.0
q2.1
q2.2
q2.3
q2.4
q2.5
q2.6
q2.7
q2.8
```

<br>

## 5. Arrow Function은 무엇인가? 함수의 선언과 표현 | (JavaScript ES6)

<br>

### ✨용어

- Funtion
    - fundamental building block in the program
    - subprogram can be used multiple times
    - performs a task or calculates a value

<br>

### 👏코드 실습

#### 1.Function declaration

- function name(param1, param2) { body... return;}
- one function === one thing
- naming: doSomething, command, verb
- e.g. createCardAndPoint -> createCard, createPoint
- function is object in JS

```jsx
function printHello() {
    console.log('Hello');
}

printHello();

function log(message) {
    console.log(message)
}
log('Hello@');
```

```jsx
Hello
Hello@
```

<br>

#### 2. Parameters

- premitive parameters: passed by value
- object parameters: passed by reference

```jsx
function changeName(obj) {
    obj.name = 'coder';
}
const nikitoe= { name: 'nikitoe' };
changeName(nikitoe);
console.log(nikitoe);
```

```jsx
{name: 'coder'}
name: "coder"
[[Prototype]]: Object
```

<br>

- Default parameters (added in ES6)

```jsx
function showMessage(message, from = 'unknown') {
    console.log(`${message} by ${from}`);
}
showMessage('Hi!')
```

```jsx
Hi! by unknown
```

<br>

#### 3. Rest parameters (added in ES6)1

```jsx
function printAll(...args) {
    for (let i = 0; i < args.length; i++) {
        console.log(args[i]);
    }

    for (const arg of args) {
        console.log(arg);
    }

    args.forEach((arg) => console.log(arg));
}
printAll('dream', 'coding', 'nikitoe')
```

```jsx
dream
coding
nikitoe
dream
coding
nikitoe
dream
coding
nikitoe
```

<br>

#### 4. Local scope

- 밖에서는 안이 보이지 않고, 안에서만 밖을 볼 수 있다

```jsx
let globalMessage = 'global' //global variable
function printMessage() {
    let message = 'hello';
    console.log(message); // local variable
    console.log(globalMessage);
}
```

<br>

#### 5. Return a value

```jsx
function sum(a, b) {
    return a + b;
}
const result = sum(1, 2); // 3
console.log(`sum : ${sum(1, 2)}`)
```

```jsx
sum : 3
```

<br>

#### 6. Early return, early exit(💡현업 tip)

```jsx
// bad
function upgreadeUser(user) {
    if (user.point > 10) {
        //long upgreade logic...
    }
}

// good
function upgreadeUser(user) {
    if (user.point <= 10) {
        return;
    }
    //long upgreade logic...
}
```

- First-class function
- functions are treated like any ohter variable
- can be assigned as a value to variable
- can be passed as an argument to other functions.
- can be returned by another function

<br>

#### 7. Function Expression

- a function declaration can be called earlier than it is defiend. (hoisted)
- a fucntion expression is created when the execution reaches it.

```jsx
const print = function () { // anonymous function
    console.log('print');
};
print();
const printAgain = print;
printAgain();
const sumAgain = sum;
console.log(sumAgain(1, 3));
```

```jsx
(2) print
4
```

<br>

```jsx
// named functinon
// better debugging in debugger's stack traces
// recursions
const printNo = function print() {
    console.log('no!');
};

randomQuiz('wrong', printYes, printNo);
randomQuiz('love you', printYes, printNo);
```

```jsx
no!
yes!
```

<br>

```jsx
// Arrow function
// always anonymous
// const simplePrint = function () {
// onsole.log('simplePrint!');
//};
const simplePrint1 = () => console.log('simplePrint!');
const add = (a, b) => a + b;
const simpleMultiply = (a, b) => {
    // do something more
    return a + b;
};
```

```jsx
// IIFE: Immediately Invoked Function Expression
(function hello() {
    console.log('IIFE');
})();
```

```jsx
IIFE
```

<br>
## 6. 클래스와 오브젝트의 차이점(class vs object), 객체지향 언어 클래스 정리 | (JavaScript ES6)

<br>

### ✨용어

- class : fields, methods의 결합체이다. 정의만하고 실제로 메모리에 올라가지 않는다.
    - template
    - declare once
    - no data in
- ojcet : class를 이용하여 실제로 data를 넣어서 만드는 것. 메모리에 올라 간다.
    - instance of a class
    - created many times
    - data in
- overriding

<br>

### 👏코드 실습

#### 1. Class declarations

```jsx
class Person {
    //constructor
    constructor(name, age) {
        //fields
        this.name = name;
        this.age = age;
    }

    //methods
    speak() {
        console.log(`${this.name} : hello!`)
    }
}

const nikitoe = new Person('nikitoe', 20);
console.log(nikitoe.name);
console.log(nikitoe.age);

nikitoe.speak();
```

```jsx
nikitoe
20
nikitoe : hello!
```

<br>

#### 2. Getter and setters

```jsx
class User {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }

    get age() {
        return this._age;
    };

    set age(value) {
        //if (value < 0) {
        //    throw Error('age can not be negative');
        //}
        this._age = value < 0 ? 0 : value;
    };
}
```

```jsx
0
```

<br>

#### 3. Fields (public, private)

```jsx
class Experiment {
    publicField = 2;
    #privateField = 0;
}
const experiment = new Experiment();
console.log(experiment.publicField);
console.log(experiment.privateField);
```

```jsx
2
undefined
```

<br>

#### 4. Static properties and methods

- Too soon!
- static은 object마다 할당되는 것이 아니라, class자체에 붙어있기 때문에
- object에 상관이없이(들어오는 data에 상관없이), 공통적으로 class에서 쓸 수 있는거라면 static과 static method를 사용함으로써 메모리의 사용을 줄일 수 있다.

```jsx
class Article {
    static publisher = 'Dream coding';

    constructor(articleNumber) {
        this.articleNumber = articleNumber;
    }

    static printPublisher() {
        console.log(Article.publisher);
    }
}

const article1 = new Article(1);
const article2 = new Article(2);
console.log(Article.publisher);
Article.printPublisher();
```

```jsx
Dream coding
Dream coding
```

<br>

#### 5. Inheritance

- a way for one class to extend another class.

```jsx
class Shape {
    constructor(width, height, color) {
        this.width = width;
        this.height = height;
        this.color = color;
    }

    draw() {
        console.log(`drawing ${this.color} color of`)
    }

    getArea() {
        return this.width * this.height;
    }
}

class Rectangle extends Shape { }
class Triangle extends Shape {
    draw() {
        super.draw();
        console.log('🔺')
    }
    getArea() {
        return (this.width * this.height) / 2;
    }
}

const rectangle = new Rectangle(20, 20, 'blue');
rectangle.draw();
console.log(rectangle.getArea());
const triangle = new Triangle(20, 20, 'red');
triangle.draw();
console.log(triangle.getArea());
```

```jsx
drawing blue color of
400
drawing red color of
🔺
200
```

<br>

#### 6. Class checking: instanceOf

```jsx
console.log(rectangle instanceof Rectangle); // true
console.log(triangle instanceof Rectangle); // false
console.log(triangle instanceof Triangle); // true
console.log(triangle instanceof Shape); // true
console.log(triangle instanceof Object); // true
```

```jsx
true
false
true
true
true
```

<br>

## 7. 오브젝트 넌 뭐니? | (JavaScript ES6)

<br>

### ✨용어

- Objects
    - one of the JavaScript's data types.
    - a collection of related data and/or functionality.
    - Nearly all objects in JavaScript are instances of Object
    - object = {key : value};

<br>

### 👏코드 실습

#### 1. Literals and properties

```jsx
const obj1 = {}; // 'object literal' syntax
const obj2 = new Object(); // 'object constructor' syntax

function print(person) {
    console.log(person.name);
    console.log(person.age);

}

const nikitoe = { name: 'nikitoe', age: 4 };
print(nikitoe);
```

```jsx
nikitoe
4
```

<br>

- with JavaScript magic (dynamically typed language)
- can add propoerties later

```jsx
nikitoe.hasJob = true;
console.log(nikitoe.hasJob);
```

```jsx
true
```

<br>

- can delete properties later

```jsx
delete nikitoe.hasJob;
console.log(nikitoe.hasJob);
```

```jsx
undefined
```

<br>

#### 2. computed properties

- key should be always string

```jsx
console.log(nikitoe.name);
console.log(nikitoe['name']);
nikitoe['hasJob'] = true;
console.log(nikitoe.hasJob);
```

```jsx
nikitoe
nikitoe
true
```

<br>

- 동적으로 key의 value를 받아올때 사용

```jsx
function printValue(obj, key) {
    console.log(obj[key]);
}

printValue(nikitoe, 'name');
printValue(nikitoe, 'age');
```

```jsx
nikitoe
4
```

<br>

#### 3. Property value shorthand

```jsx
const person1 = { name: 'bob', age: 4 };
const person2 = { name: 'steve', age: 15 };
const person3 = { name: 'dave', age: 5 };
const person4 = new Person('nikitoe', 20);
console.log(person4);
```

```jsx
Person {name: 'nikitoe', age: 20}
age: 20
name: "nikitoe"
[[Prototype]]: Object
```

<br>

#### 4. in operator: property existence check (key in obj)

```jsx
console.log('name' in nikitoe);
console.log('age' in nikitoe);
console.log('random' in nikitoe);
console.log(nikitoe.random);
```

```jsx
true
true
false
undefined
```

<br>

#### 5. for..in vs for..of

- for (key in obj)

```jsx
for (key in nikitoe) {
    console.log(key);
}
```

```jsx
name
age
hasJob
```

<br>

- for (value of iterable)

```jsx
const array = [1, 2, 4, 5];
for (value of array) {
    console.log(value);
}
```

```jsx
1
2
4
5
```

<br>

#### 6. Fun cloning

- Object.assign(dest, [obj1, obj2, obj3...])

```jsx
const user = { name: 'nikitoe', age: '20' }
const user2 = user;
user2.name = 'coder';
console.log(user);

// old way
const user3 = {};
for (key in user) {
    user3[key] = user[key];
}
console.log(user3);

// good way
const user4 = Object.assign({}, user);
console.log(user4);
```

```jsx
{name: 'coder', age: '20'}
age: "20"
name: "coder"
[[Prototype]]: Object

{name: 'coder', age: '20'}
age: "20"
name: "coder"
[[Prototype]]: Object

{name: 'coder', age: '20'}
age: "20"
name: "coder"
[[Prototype]]: Object
```

<br>

- another example

```jsx
const fruit1 = { color: 'red' };
const fruit2 = { color: 'blue', size: 'big' };
const mixed = Object.assign({}, fruit1, fruit2);
console.log(mixed.color);
console.log(mixed.size);
```

```jsx
blue
big
```

<br>

## 8. 배열 제대로 알고 쓰자. 자바스크립트 배열 개념과 APIs 총정리 | (JavaScript ES6 )

<br>

### ✨용어

- 자료 구조
    - 어떤 방식과 형식으로 data를 담아 넣느냐에 따라 많은 type이 존재한다.
    - 비슷한 type의 object들을 묶어 놓은 것.
- 알고리즘
- 검색, 삽입, 삭제, 정렬

<br>

### 👏코드 실습

#### 1. Declaration

Array✨

```jsx
const arr1 = new Array();
const arr2 = [1, 2];
```

<br>

#### 2. Index position

```jsx
const fruits = ['🍎', '🍌'];
console.log(fruits);
console.log(fruits.length);
console.log(fruits[0]);
console.log(fruits[1]);
console.log(fruits[fruits.length - 1]);
```

```jsx
(2) ['🍎', '🍌']
2
🍎
🍌
🍌
```

<br>

#### 3. Looping over an array

- print all fruits
- a. for

```jsx
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```

```jsx
🍎
🍌
```

<br>

- b. for of

```jsx
for (let fruit of fruits) {
    console.log(fruit);
}
```

```jsx
🍎
🍌
```

<br>

- c. forEach
- forEach는 배열안에 들어있는 value들 마다 자신이 전달한 함수를 출력 함.

```jsx
fruits.forEach((fruit) => console.log(fruit));
```

```jsx
🍎
🍌
```

<br>

#### 4. addtio, deletion, copy

- push: add an item

```jsx
fruits.push('🍇', '🍓');
console.log(fruits);
```

```jsx
(4) ['🍎', '🍌', '🍇', '🍓']
```

<br>

- pop: remove an item from the end

```jsx
fruits.pop();
fruits.pop();
console.log(fruits);
```

```jsx
(2) ['🍎', '🍌']
```

<br>

- unshift: add an item to the begining

```jsx
fruits.unshift('🍇', '🍓');
console.log(fruits);
```

```jsx
(4) ['🍇', '🍓', '🍎', '🍌']
```

<br>

- shift: remove an item from the begining

```jsx
fruits.shift();
fruits.shift();
console.log(fruits);
```

```jsx
(2) ['🍎', '🍌']
```

📒note!! shift, unshift are slower than pop, push

<br>

- splice: remove an item by index position

```jsx
fruits.push('🍇', '🍓', '🍒')
console.log(fruits);
fruits.splice(1, 1);
console.log(fruits);
fruits.splice(1, 1, '🍏', '🥝');
console.log(fruits);
```

```jsx
(5) ['🍎', '🍌', '🍇', '🍓', '🍒']
(4) ['🍎', '🍇', '🍓', '🍒']
(5) ['🍎', '🍏', '🥝', '🍓', '🍒']
```

<br>

- combine two arrays

```jsx
const fruits2 = ["🍍", "🍋"];
const newFruits = fruits.concat(fruits2);
console.log(newFruits);
```

```jsx
(7) ['🍎', '🍏', '🥝', '🍓', '🍒', '🍍', '🍋']
```

<br>

#### 5. searching

- indexOf: find the index

```jsx
console.log(fruits);
console.log(fruits.indexOf("🍎"));
console.log(fruits.indexOf("🥝"));
console.log(fruits.indexOf("🥜"));
```

```jsx
(5) ['🍎', '🍏', '🥝', '🍓', '🍒']
0
2
-1
```

<br>

- includes

```jsx
console.log(fruits.includes("🍎"));
console.log(fruits.includes("🥜"));
```

```jsx
true
false
```

<br>

- lastIndexOf

```jsx
fruits.push("🍎");
console.log(fruits);
console.log(fruits.indexOf("🍎"));
console.log(fruits.lastIndexOf("🍎"));
```

```jsx
(6) ['🍎', '🍏', '🥝', '🍓', '🍒', '🍎']
0
5
```

<br>

## 9. 유용한 10가지 배열 함수들. Array APIs 총정리 | ( JavaScript ES6)

<br>

### ✨용어

- join()
- split()
- reserve()
- slice()
- find()
- filter()
- map()
- some()
- every()
- reduce()
- reduceRight()
- score()

<br>

### 👏코드 실습

#### Q1. make a string out of an array

```jsx
{
    const fruits = ['apple', 'banana', 'orange'];
    const result = fruits.join(",");
    console.log(result);
}
```

```jsx
apple,banana,orange
```

<br>

#### Q2. make an array out of a string

```jsx
{
    const fruits = '🍎, 🥝, 🍌, 🍒';
    const result = fruits.split(",", 4);
    console.log(result);
}
```

```jsx
(2) ['🍎', ' 🥝']
```

<br>

#### Q3. make this array look like this: [5, 4, 3, 2, 1]

```jsx
{
    const array = [1, 2, 3, 4, 5];
    const result = array.reverse();
    console.log(result);
    console.log(array);
}
```

```jsx
(5) [5, 4, 3, 2, 1]
(5) [5, 4, 3, 2, 1]
```

<br>

#### Q4. make new array without the first two elements

```jsx
{
    const array = [1, 2, 3, 4, 5];

    // incorrect
    // splice: 배열 자체를 수정한다.
    //const result = array.splice(0, 2);
    //console.log(result);
    //console.log(array);

    // correct
    // slice: 배열에서 원하는 부분만 return할 수 있다.
    const result = array.slice(2, 5);
    console.log(result);
    console.log(array);
}
```

```jsx
(3) [3, 4, 5]
(5) [1, 2, 3, 4, 5]
```

<br>

#### Q5 ~ Q10. 복합 문제

```jsx
class Student {
    constructor(name, age, enrolled, score) {
        this.name = name;
        this.age = age;
        this.enrolled = enrolled;
        this.score = score;
    }
}
const students = [
    new Student('A', 29, true, 45),
    new Student('B', 28, false, 80),
    new Student('C', 30, true, 90),
    new Student('D', 40, false, 66),
    new Student('E', 18, true, 88),
];
```

##### Q5. find a student with the score 90

- find(): 배열들의 요소마다 호출이 되고, 각각 하나씩 검사하여 해당 하는 값을 return 해준다.

```jsx
{
    const result = students.find((student) => student.score === 90);
    console.log(result);
}
```

```jsx
Student {name: 'C', age: 30, enrolled: true, score: 90}
age: 30
enrolled: true
name: "C"
score: 90
[[Prototype]]: Object
```

<br>

##### Q6. make an array of enrolled students

- filter(): 원하는 값만 받아 올 수 있다.

```jsx
{
    const result = students.filter((student) => student.enrolled);
    console.log(result);
}
```

```jsx
(3) [Student, Student, Student]
0: Student {name: 'A', age: 29, enrolled: true, score: 45}
1: Student {name: 'C', age: 30, enrolled: true, score: 90}
2: Student {name: 'E', age: 18, enrolled: true, score: 88}
length: 3
[[Prototype]]: Array(0)
```

<br>

##### Q7. make an array containing only the students' scores, result should be: [45, 80, 90, 66, 88]

- map(): 배열안에 있는 모든 요소들을 전달해준 콜백 함수로 콜백 하면서, 콜백 함수에서 가공되어진 값들로 대체되어 지는 것
- 💡tip: 콜백 함수의 인자는 이해하기 쉬운 문자를 사용한다.

```jsx
{
    const result = students.map((student) => student.score);
    console.log(result);
}
```

```jsx
(5) [45, 80, 90, 66, 88]
0: 45
1: 80
2: 90
3: 66
4: 88
length: 5
[[Prototype]]: Array(0)
```

<br>

##### Q8. check if there is a student with the score lower than 50

- some(): 하나의 요소라도 충족 되었을때 출력한다.
- every(): 모든 요소들이 충족되었을때만 출력된다.

```jsx
{
    const result = students.some((student) => student.score < 50);
    console.log(result);

    const result2 = !students.every((student) => student.score >= 50);
    console.log(result2);

}
```

```jsx
true
true
```

<br>

##### Q9. compute students' average score

- reduce(): 원하는 시작점부터, 모든 배열을 돌면서 어떤 값을 누적할 때 사용한다.
- reduceRight(): 배열의 끝에서 부터 시작하고 누적해 간다.

```jsx
{
    const result = students.reduce((prev, curr) => prev + curr.score, 0);
    console.log(result / students.length);
}
```

```jsx
73.8
```

<br>

##### Q10. make a string containing all the scores, result should be: '45, 80, 90, 66, 88'

```jsx
{
    const result = students
        .map((student) => student.score)
        .filter((score) => score >= 50)
        .join();
    console.log(result);
}
```

```jsx
80,90,66,88
```

<br>

##### Bonus! do Q10 sorted in ascending order, result should be: '45, 66, 80, 88, 90'

```jsx
{
    const result = students
        .map((student) => student.score)
        .sort((a, b) => a - b)
        .join();
    console.log(result);
}
```

```jsx
45,66,80,88,90
```

<br>

## 10. JSON 개념 정리 와 활용방법 및 유용한 사이트 공유 JavaScript JSON | (JavaScript ES6)

<br>

### ✨용어

- AJAX(Asynchronous JavaScript And XML)
    - 웹페이지에서 동적으로 서버에게 data를 주고 받을 수 있는 기술
- XHR(XMLHttpRequest)
- fetch() API
- JSON(JavaScript Object Notation)
    - data를 주고 받을 수 있는 가장 간단한 포멧
    - text 기반으로 벼움
    - 가독성이 좋음
    - key와 value로 이루어져 있음
    - 대부분의 프로그래밍 언어와 플랫폼에 상관없이 적용 가능👍👍👍
- Overloading:
    - 함수 이름은 동일하지만 어떤 파라미터를 전달하느냐, 몇개의 파라미터를 전달하느냐에 따라서 각각 다른 방식으로 호출이 가능

<br>

- JSON에 대해 조금더 공부를 하고 싶으시면
    - MDN: [https://developer.mozilla.org/en-US/d...](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
    - JavaScript.info: [https://javascript.info/json](https://javascript.info/json)
    - JavaScript.info 한국어: [https://ko.javascript.info/json](https://ko.javascript.info/json)
- 유용한 사이트
    - JSON Diff checker: [http://www.jsondiff.com/](http://www.jsondiff.com/)
    - JSON Beautifier/editor: [https://jsonbeautifier.org/](https://jsonbeautifier.org/)
    - JSON Parser: [https://jsonparser.org/](https://jsonparser.org/)
    - JSON Validator: [https://tools.learningcontainer.com/j...](https://tools.learningcontainer.com/json-validator/)

<br>

### 👏코드 실습

#### 1. Object to JSON

- stringfy(obj)

```jsx
let json = JSON.stringify(true);
console.log(json);

json = JSON.stringify(['apple', 'banana']);
console.log(json);

const rabbit = {
    name: 'tori',
    color: 'white',
    size: null,
    birthDate: new Date(),
    jump: () => {
        console.log(`${this.name} can jump!`);
    },
}

json = JSON.stringify(rabbit);
console.log(json);

json = JSON.stringify(rabbit, ['name', 'color']);
console.log(json);

json = JSON.stringify(rabbit, (key, value) => {
    console.log(`key: ${key}, value: ${value}`);
    return key === 'name' ? 'nikitoe' : value;
});
console.log(json);
```

```jsx
true
["apple","banana"]
{"name":"tori","color":"white","size":null,"birthDate":"2022-01-22T06:49:41.370Z"}
{"name":"tori","color":"white"}
key: , value: [object Object]
key: name, value: tori
key: color, value: white
key: size, value: null
key: birthDate, value: 2022-01-22T06:49:41.370Z
key: jump, value: () => {
        console.log(`${this.name} can jump!`);
    }
{"name":"nikitoe","color":"white","size":null,"birthDate":"2022-01-22T06:49:41.370Z"}
```

<br>

#### 2. JSON to Object

```jsx
json = JSON.stringify(rabbit);
const obj = JSON.parse(json, (key, value) => {
    console.log(`key: ${key}, value: ${value}`);
    return key === 'birthDate' ? new Date(value) : value;
});
console.log(obj);
rabbit.jump();
// obj.jump();

console.log(rabbit.birthDate.getDate());
console.log(obj.birthDate.getDate());
```

```jsx
key: name, value: tori
key: color, value: white
key: size, value: null
key: birthDate, value: 2022-01-22T06:50:36.293Z
key: , value: [object Object]
{name: 'tori', color: 'white', size: null, birthDate: Sat Jan 22 2022 15:50:36 GMT+0900 (한국 표준시)}birthDate: Sat Jan 22 2022 15:50:36 GMT+0900 (한국 표준시) {}color: "white"name: "tori"size: null[[Prototype]]: Object
 can jump!
22
22
```

<br>

## 11. 비동기 처리의 시작 콜백 이해하기, 콜백 지옥 체험 😱 JavaScript Callback | (JavaScript ES6)

<br>

### ✨용어

- Synchronous
- Asynchronous callback
- hoisting
    - var, function declaration등 함수 선언들이 자동적으로 제일 위로 올라가는 것
- callback 함수

<br>

### 👏코드 실습

```jsx
// Synchronous callback
function printImmediately(print) {
    print();
}

// Asynchronous callback
function printWithDelay(print, timeout) {
    setTimeout(print, timeout);
}
```

- JavaScript is synchronous.
- Exceute the code block by order after hoisting.

```jsx
console.log('1');   // 동기
setTimeout(() => console.log('2'), 1000); // 비동기
console.log('3'); // 동기
printImmediately(() => console.log('hello')); // 동기
printWithDelay(() => console.log('async callback'), 2000); // 비동기
```

```jsx
1
3
hello
2
async callback
```

<br>

- Callback Hell example

```jsx
class UserStorage {
    loginUser(id, password, onSucess, onError) {
        setTimeout(() => {
            if (
                (id === 'nikitoe' && password === 'dream') ||
                (id === 'coder' && password === 'academy')
            ) {
                onSucess(id);
            } else {
                onError(new Error('not found'));
            }
        }, 2000);
    }

    getRoles(user, onSucess, onError) {
        setTimeout(() => {
            if (user === 'nikitoe') {
                onSucess({ name: 'nikitoe', role: 'admin' });
            } else {
                onError(new Error('no access'));
            }
        });
    }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');

userStorage.loginUser(
    id,
    password,
    (user) => {
        userStorage.getRoles(
            user,
            (userWithRole) => {
                alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role}`);
            },
            (error) => { }
        );
    },
    (error) => {
        console.log(error)
    }
);
```
![11-id](/assets/img/blog/study/javascript/study-javascript-11-id.jpg){: width="400" height="400"}

![11-password](/assets/img/blog/study/javascript/study-javascript-11-password.jpg){: width="400" height="400"}

![11-sucess](/assets/img/blog/study/javascript/study-javascript-11-sucess.jpg){: width="400" height="400"}
<br>

## 12. 프로미스 개념부터 활용까지 JavaScript Promise | (JavaScript ES6)

<br>

### ✨용어

- Promise
    - 비동기를 간편하게 처리할 수 있도록 도와주는 Object
    - state

<br>

### 👏코드 실습

#### 1. Producer

- when new Promise is created, the executor runs automatically.

```jsx
const promise = new Promise((resolve, reject) => {
    // doing some heavy work (network, read files)
    console.log('doing something...');
    setTimeout(() => {
        resolve('nikitoe');
        // reject(new Error('no network'))
    }, 2000);
});
```

```jsx
doing something...
```

<br>

#### 2. Consumers: then, catch, finally

```jsx
promise
    .then((value) => {
        console.log(value);
    })
    .catch((error) => {
        console.log(error);
    })
    .finally(() => {
        console.log('finally');
    });
```

```jsx
nikitoe
finally
```

<br>

#### 3. Promise changing

```jsx
const fetchNumber = new Promise((resolve, reject) => {
    setTimeout(() => resolve(1), 1000);
});

fetchNumber
    .then(num => num * 2)
    .then(num => num * 3)
    .then(num => {
        return new Promise((resolve, reject) => {
            setTimeout(() => resolve(num - 1), 1000);
        });
    })
    .then(num => console.log(num));
```

```jsx
5
```

<br>

#### 4. Error Handling

```jsx
const getHen = () =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve('🐔'), 1000);
    });
const getEgg = hen =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve(`${hen} => 🥚`), 1000);
    });
const cook = egg =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve(`${egg} => 🍤`), 1000);
    });

getHen() //
    .then(getEgg)
    .then(cook)
    .then(console.log)
    .catch(console.log);
```

```jsx
🐔 => 🥚 => 🍤
```

```jsx
const getHen = () =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve('🐔'), 1000);
    });
const getEgg = hen =>
    new Promise((resolve, reject) => {
        setTimeout(() => reject(new Error(`error! ${hen} => 🥚`)), 1000);
    });
const cook = egg =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve(`${egg} => 🍤`), 1000);
    });

getHen() //
    .then(getEgg)
    .catch(error => {
        return '🥖';
    })
    .then(cook)
    .then(console.log)
    .catch(console.log);
```

```jsx
🥖 => 🍤
```

<br>

## 13. 비동기의 꽃 JavaScript async 와 await 그리고 유용한 Promise APIs | (JavaScript ES6)

<br>

### ✨용어

- async-await
    - clear sytle of using promise :)
- pending

<br>

### 👏코드 실습

#### 1. async

```jsx
async function fetchUser() {
    // do network request in 10 secs...
    return 'nikitoe';
}

const user = fetchUser();
user.then(console.log);
console.log(user);
```

```jsx
Promise {<fulfilled>: 'nikitoe'}
```

<br>

#### 2. await⭐⭐⭐⭐⭐

```jsx
function delay(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
    await delay(2000);
    return '🍎';
}

async function getBanana() {
    await delay(1000);
    return '🍌';
}

async function pickFruits() {
    const applePromise = getApple();
    const bananaPromise = getBanana();
    const apple = await applePromise;
    const banana = await bananaPromise;
    return `${apple} + ${banana}`;
}

pickFruits().then(console.log);
```

```jsx
🍎 + 🍌
```

<br>

#### 3. useful Promise APIs ⭐⭐⭐⭐⭐

```jsx
function pickAllFruits() {
    return Promise.all([getApple(), getBanana()])
        .then(fruits => fruits.join(' + '));
}

pickAllFruits().then(console.log);

function pickOnlyOne() {
    return Promise.race([getApple(), getBanana()]);
}

pickOnlyOne().then(console.log);
```

```jsx
🍌
🍎 + 🍌
```

<br>

#### 💡tip: promise, async와 await를 사용하여 12번의 hellcode example의 callback지옥을 해결할 수 있다.

```jsx
// Callback Hell example
class UserStorage {
    loginUser(id, password, onSucess, onError) {
        setTimeout(() => {
            if (
                (id === 'nikitoe' && password === 'dream') ||
                (id === 'coder' && password === 'academy')
            ) {
                onSucess(id);
            } else {
                onError(new Error('not found'));
            }
        }, 2000);
    }

    getRoles(user, onSucess, onError) {
        setTimeout(() => {
            if (user === 'nikitoe') {
                onSucess({ name: 'nikitoe', role: 'admin' });
            } else {
                onError(new Error('no access'));
            }
        });
    }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');

userStorage.loginUser(
    id,
    password,
    (user) => {
        userStorage.getRoles(
            user,
            (userWithRole) => {
                alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role}`);
            },
            (error) => { }
        );
    },
    (error) => {
        console.log(error)
    }
);
```

```jsx
// good code
class UserStorage {
    loginUser(id, password) {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                if (
                    (id === 'ellie' && password === 'dream') ||
                    (id === 'coder' && password === 'academy')
                ) {
                    resolve(id);
                } else {
                    reject(new Error('not found'));
                }
            }, 2000);
        });

    }

    getRoles(user) {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                if (user === 'ellie') {
                    resolve({ name: 'ellie', role: 'admin' });
                } else {
                    reject(new Error('no access'));
                }
            }, 1000);
        });
    }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');

async function userCheck() {
    try {
        const userid = await userStorage.loginUser(id, password);
        const user = await userStorage.getRoles(userid);
        alert(`Hello ${user.name}, you have a ${user.role} role`)
    } catch (error) {
        console.log(error)
    };
}
userCheck();
```