---
layout: post
title: Study-JavaScript-Basic
image: /assets/img/blog/study/background-javascript.png
sitemap: false
hide_last_modified: false
categories:
  - study
  - javascript
---

# [JavaScript] 기초

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

#### 1.*Use stricit*
  - *added in ES 5*
  - *use this for Vanila Javascript.*
    
    ```jsx
    'use strict';
    ```
    
#### 2. *Variable, rw (read/write)*
  - *let (added in ES6)*
    
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
    
#### 3. *Contant, r (read only)*
  - *use const whenever possible*
  - *only use let if variable needs to change*
    
    ```jsx
    const daysInWeek = 7;
    const maxNumber = 5;
    ```
    
  - Note!!👌
    - *Immutable data types: primitive types, frozen objects (i.e. object.freeze())*
    - *Mutable data types: all objects by default are mutable in JS*
    - *favor immutable data type always for a few reasons:*
    - *security*
    - *thread safety*
    - *reduce human mistakes*
    
    <br>
    
#### 4. *Variable types*
  - *primitive, single item: number, string, boolean, null, undefied, symbol*
  - *object, box container*
  - *function, first-class function*
    
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
    
  - *number - sepcial numeric values: infinity, -infinity, NaN*
    
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
    
  - *bigInt (fairly new, dont use it yet)*
    
    ```jsx
    const bigInt = 123123123123123143241342353902194n; // over (-2**53~2*53)
    console.log(`value: ${bigInt}, type: ${typeof bigInt}`)
    Number.MAX_SAFE_INTEGER;
    ```
    ```jsx
    value: 123123123123123143241342353902194, type: bigint
    ```
    
    <br>
    
  - *string*
    
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
    
  - *boolean*
        - *false: 0, null, undefined, NaN, ‘’*
        - *true: any other value*
    
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
    
  - *null*
    
    ```jsx
    let nothing = null;
    console.log(`value: ${nothing}, type: ${typeof nothing}`);
    ```
    ```jsx
    value: null, type: object
    ```
    
    <br>
    
  - *undefined*
    
    ```jsx
    let x;
    console.log(`value: ${x}, type: ${typeof x}`);
    ```
    ```jsx
    value: undefined, type: undefined
    ```
    
    <br>
    
  - *symbol, create unique identifiers for objects*
    
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
    
  - *object, real-life object, data structure*
    
    ```jsx
    const nikite = { name: 'nikite', age: 20 };
    ```
    
#### 5. *Dynamic typing: dynamically typed language*
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

- *object-oriendted programming*
- *class : templawte*
- *object : instance of a class*
- *JavaScript classes*
- *introduced in ES6*
- *syntactical sugar over prototype-based inheritance*

#### 1. *Increment and decrement operators*

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

#### 2. *Assignment operators*

```jsx
let x = 3;
let y = 6;
x += y; // x= x + y;
x -= y;
x *= y;
x / + y;
```

<br>

#### 3. *Logical operators: || (or), && (and), ~ (not)*

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

#### 4*. Equality*

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

#### 5. *Conditional operators: if*

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

#### 6. *Ternary operatoer: ?*

- *condition ? value1 : value2;*

```jsx
console.log(nickname === 'nikitoe' ? 'yes' : 'no')
```

```jsx
yes
```

<br>

#### 7. *Switch statement*

- *use for multiple if checks*
- *use for enum-like value check*
- *use for multiple type checks in TS*

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

#### 8. *Loops*

- *while loop, while the condition is truthy,*
- *body code is executed.*

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

- *break, continue*

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

- *Funtion*
    - *fundamental building block in the program*
    - *subprogram can be used multiple times*
    - *performs a task or calculates a value*

<br>

### 👏코드 실습

#### 1. *Function declaration*

- *function name(param1, param2) { body... return;}*
- *one function === one thing*
- *naming: doSomething, command, verb*
- *e.g. createCardAndPoint -> createCard, createPoint*
- *function is object in JS*

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

#### 2. *Parameters*

- *premitive parameters: passed by value*
- *object parameters: passed by reference*

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

- *Default parameters (added in ES6)*

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

#### 3. *Rest parameters (added in ES6)1*

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

#### 4. *Local scope*

- *밖에서는 안이 보이지 않고, 안에서만 밖을 볼 수 있다/*

```jsx
let globalMessage = 'global' //global variable
function printMessage() {
    let message = 'hello';
    console.log(message); // local variable
    console.log(globalMessage);
}
```

<br>

#### 5. *Return a value*

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

#### 6. *Early return, early exit(💡현업 tip)*

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

- *First-class function*
- *functions are treated like any ohter variable*
- *can be assigned as a value to variable*
- *can be passed as an argument to other functions.*
- *can be returned by another function*

<br>

#### 7. *Function Expression*

- *a function declaration can be called earlier than it is defiend. (hoisted)*
- *a fucntion expression is created when the execution reaches it.*

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

#### 1. *Class declarations*

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

#### 2. *Getter and setters*

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

#### 3. *Fields (public, private)*

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

#### 4. *Static properties and methods*

- *Too soon!*
- *static은 object마다 할당되는 것이 아니라, class자체에 붙어있기 때문에*
- *object에 상관이없이(들어오는 data에 상관없이), 공통적으로 class에서 쓸 수 있는거라면 static과 static method를 사용함으로써 메모리의 사용을 줄일 수 있다.*

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

#### 5. *Inheritance*

- *a way for one class to extend another class.*

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

#### 6. *Class checking: instanceOf*

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

- *Objects*
    - *one of the JavaScript's data types.*
    - *a collection of related data and/or functionality.*
    - *Nearly all objects in JavaScript are instances of Object*
    - *object = {key : value};*

<br>

### 👏코드 실습

#### 1. *Literals and properties*

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

- *with JavaScript magic (dynamically typed language)*
- *can add propoerties later*

```jsx
nikitoe.hasJob = true;
console.log(nikitoe.hasJob);
```

```jsx
true
```

<br>

- *can delete properties later*

```jsx
delete nikitoe.hasJob;
console.log(nikitoe.hasJob);
```

```jsx
undefined
```

<br>

#### 2. *computed properties*

- *key should be always string*

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

- *동적으로 key의 value를 받아올때 사용*

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

#### 3. *Property value shorthand*

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

#### 4. *in operator: property existence check (key in obj)*

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

#### 5. *for..in vs for..of*

- *for (key in obj)*

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

- *for (value of iterable)*

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

#### 6. *Fun cloning*

- *Object.assign(dest, [obj1, obj2, obj3...])*

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

- *another example*

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

#### 1. *Declaration*

*Array✨*

```jsx
const arr1 = new Array();
const arr2 = [1, 2];
```

<br>

#### 2. *Index position*

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

#### 3. *Looping over an array*

- *print all fruits*
- *a. for*

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

- *b. for of*

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

- *c. forEach*
- *forEach는 배열안에 들어있는 value들 마다 자신이 전달한 함수를 출력 함.*

```jsx
fruits.forEach((fruit) => console.log(fruit));
```

```jsx
🍎
🍌
```

<br>

#### 4. *addtio, deletion, copy*

- *push: add an item*

```jsx
fruits.push('🍇', '🍓');
console.log(fruits);
```

```jsx
(4) ['🍎', '🍌', '🍇', '🍓']
```

<br>

- *pop: remove an item from the end*

```jsx
fruits.pop();
fruits.pop();
console.log(fruits);
```

```jsx
(2) ['🍎', '🍌']
```

<br>

- *unshift: add an item to the begining*

```jsx
fruits.unshift('🍇', '🍓');
console.log(fruits);
```

```jsx
(4) ['🍇', '🍓', '🍎', '🍌']
```

<br>

- *shift: remove an item from the begining*

```jsx
fruits.shift();
fruits.shift();
console.log(fruits);
```

```jsx
(2) ['🍎', '🍌']
```

📒*note!! shift, unshift are slower than pop, push*

<br>

- *splice: remove an item by index position*

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

- *combine two arrays*

```jsx
const fruits2 = ["🍍", "🍋"];
const newFruits = fruits.concat(fruits2);
console.log(newFruits);
```

```jsx
(7) ['🍎', '🍏', '🥝', '🍓', '🍒', '🍍', '🍋']
```

<br>

#### 5. *searching*

- *indexOf: find the index*

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

- *includes*

```jsx
console.log(fruits.includes("🍎"));
console.log(fruits.includes("🥜"));
```

```jsx
true
false
```

<br>

- *lastIndexOf*

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