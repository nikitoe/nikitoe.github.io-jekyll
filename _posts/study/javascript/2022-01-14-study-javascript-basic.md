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
    const ellie = { name: 'ellie', age: 20 };
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

