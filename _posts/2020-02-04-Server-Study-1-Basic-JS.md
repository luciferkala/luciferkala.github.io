---
layout: post
title: "1. Server Study - Basic JavaScript"
date: 2020-02-04
excerpt: "서버 스터디 JavaScript 기초"
tags: [Development, Node.js, JavaScript, ECMA2015, Learn Server, Server Study]
comments: true
---

# 서버 스터디를 위한 기초 자바스크립트

## 자바스크립트(JavaScript)란?

자바스크립트는 웹에서 사용하기 위해 고안된 언어에서 시작하였다.
자바스크립트는 웹 문서 내의 HTML/CSS 요소를 동적으로 변경하기 위한 언어이다.
그러나 현재는 웹 브라우저를 넘어서 어플리케이션을 구현하는데도 사용되는 언어이다.

### 자바스크립트의 특징

자바스크립트는 다음과 같은 특징이 있다.

-   인터프리터 언어이다.
-   비동기 I/O 기반이다.
-   싱글 스레드로 실행된다. (자세한 설명이 필요)
-   프로토타입 기반 언어이다.
-   함수가 1급 객체이다.

이것들이 무엇인지 하나하나 알아보자.

---

#### 인터프리터 언어이다

자바스크립트는 인터프리터 언어(Interpreter Language)이다.
인터프리터 언어는 컴파일러 언어와 다른 문법을 가진다.

컴파일러 언어의 대표적인 예시로는 **C, C++, Java** 등이 있다.
컴파일러 언어는 코드를 실행하기 전에 컴파일러를 실행시킨다.
실행된 컴파일러가 이를 기계어로 변환하고 실행파일을 만든 후 실행시킨다.
따라서, 한번 컴파일을 하면 실행속도가 빠르나 코드 작성시 데이터의 유형 및 메모리 크기를 지정해주어야 한다.

반면에, 인터프리터 언어의 대표적인 예시로는 **Python, JavaScript** 가 있다.
인터프리터 언어의 인터프리터는 **통역자(Interpreter)** 라는 뜻을 가지고 있으며,
이는 코드를 실행할 때(런타임 시), 한줄한줄 즉각적으로 읽어가면서 코드를 실행한다.
따라서, 코드의 유형을 정해주지 않아도 알아서 알맞는 자료형을 집어넣어서 실행해준다.
그러나, 실행 속도는 컴파일 언어보다는 느린편이다.

#### 비동기 I/O 기반이다.

자바스크립트는 I/O 기반이다.
이는 아래에서 설명할 싱글 스레드를 가지는 것과 상통하는 특징이다.
싱글 스레드와 비동기 I/O를 가지는 이유는 자바스크립트가 탄생한 웹 환경을 생각해보면 자연스럽게 이해가 된다.

> 예를 들어서, 네이버 뉴스 페이지에 접속했다고 생각해보자.
> 뉴스 데이터베이스에는 1억개의 뉴스가 저장되어있는데, 네이버 서버가 이를 불러와서 접속한 클라이언트에게 뉴스를 보여주려 한다고 생각해보자.
> 이 행동이 동기식으로 실행이 된다고 하면, 웹 브라우저는 1억개의 뉴스를 가져오기 전까지 어떠한 화면도 보여줄 수가 없다.
> 왜냐하면 1억개의 뉴스를 불러오는 작업이 끝나야 웹 페이지를 보여줄 수 있기 때문이다.
> 이를 받아들이는 사용자는 원인을 모르고 페이지가 오류가 있다고 생각할 것이다.
> 따라서, 이러한 언어의 기반을 생각해 보았을 떄, 자바스크립트는 비동기 I/O를 지니게 되었다.

이러한 언어의 특성상 자바스크립트는 비동기 I/O를 기반으로 하는 언어가 되었다.

#### 싱글 스레드 기반이다.

자바스크립트는 비동기 I/O를 구현하기 위해서 싱글 스레드를 사용하는 방식을 채택했다.
웹 브라우저의 특성상 비동기 I/O를 구현하기 위해 멀티 스레드를 사용하면 고려해야 할 사항도 많고, 멀티 스레드 환경에서 사용되는 쓰레드가 쉬는 자원도 무시할 수 없기 때문이다.
따라서 이를 위해서 싱글 스레드를 사용하였다.

싱글 스레드를 사용하면 멀티 스레드에서 겪는 다양한 선결과제들을 고려할 필요가 없어지기 때문에, 사용자 역시 비동기 처리를 간단하게 행할 수 있으며, 싱글 스레드를 최대한 효율적으로 사용하기 때문에 성능 역시 뒤쳐지지 않는다.

[자세한 내용은 다음 링크 참조 - 1 : React Pattern](./2020-01-13-1.Nodejs-Design-Pattern-introduction-2.md)
[자세한 내용은 다음 링크 참조 - 2 : Event Emitter](2020-01-19-2.Nodejs-필수-패턴-3.md)

#### 프로토타입(Prototype) 기반이다.

자바스크립트는 ECMA2015(통칭 ES6)부터 클래스 문법을 지원한다.
그래서 객체와 상속구조를 클래스 문법을 이용하여 구현할 수 있지만, 사실 내부적으로는 프로토타입 문법으로 구현된다. (그리고 정말 엄밀히 말하면 상속이 없는 것이긴 하다.)

따라서 우리는 프로토타입을 알아야한다.

프로토타입(Prototype)은 원형(Original)이라는 뜻을 가진다.
사실 자바스크립트의 프로토타입은 **디자인 패턴** 의 프로토타입 패턴이 기반이다.

프로토타입 패턴이란, 어떤 객체를 생성하는 것이 비용이 많이 들 경우에 객체를 복사하여 다른 객체를 만드는 패턴을 의미한다.
이를 이용하면 객체를 만드는 비용을 절약할 수 있으며, 객체를 프로토타입으로 연결하여 동적인 객체구조를 형성할 수 있다.

일단은 자바스크립트가 프로토타입 기반 언어이며, 자바나 다른 객체지향 언어와는 조금 다른 특성을 가진다는 것까지만 이해 해보자.

#### 함수가 1급 객체이다.

자바스크립트에서 또 하나 이질적인 것은 함수가 1급 객체라는 것이다.
1급 객체라는 것은 다음과 같은 특성을 가진다.

> 1. 모든 요소는 함수의 실제 매개변수가 될 수 있다.
> 2. 모든 요소는 함수의 반환 값이 될 수 있다.
> 3. 모든 요소는 할당 명령문의 대상이 될 수 있다.
> 4. 모든 요소는 동일 비교의 대상이 될 수 있다.

[출처 : 위키피디아 일급 객체 : https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B8%89\_%EA%B0%9D%EC%B2%B4](https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B8%89_%EA%B0%9D%EC%B2%B4)

따라서 자바스크립트에서는 함수도 1급 객체에 해당하여 다음과 같은 항목들이 모두 가능하다.

---

## 자바스크립트 문법

기본적인 언어의 특성에 대해서 알아보았으니, 다음으로는 문법을 알아보자.
문법은 Java와 비교를 해보며 어떤 것이 다른지 확인 해보자.

언어의 설명하는 요소 순서는 다음을 참고하였다.
[참고 링크 : https://learnjs.vlpt.us/useful/04-default-function-params.html](https://learnjs.vlpt.us/useful/04-default-function-params.html)

---

### Hello, World!

다음과 같은 코드를 쳐보자.

```javascript
// JavaScript Code
console.log("Hello, World!");
```

그러면 다음과 같은 결과가 나타날 것이다.

```
Hello, World!
```

이는 Java의 다음과 같다.

```java
// Java Code
System.out.println("Hello, World!");
```

---

### 자료형의 종류

자바스크립트에서는 자료형은 다음과 같은 종류들이 있다.

-   Number
    -   모든 숫자 자료형은 전부 Number이다.
-   String
    -   모든 문자열은 전부 String이다.
-   Boolean
    -   true, false를 나타낸다.
    -   비교 연산에서 0, null, undefined도 false를 나타낸다.
-   function
    -   함수이다.
    -   함수도 1급 객체이기 때문에 변수에 할당이 가능하다.
    -   참조형 변수이다.
-   Array
    -   배열이다.
    -   참조형 변수이다.
-   Object
    -   객체이다.
-   undefined
    -   null과 동일하게 없는 값을 나타낸다.
    -   예상치 못한 없는 값은 undefined이다.
-   null
    -   undefined와 마찬가지로 없는 값을 나타낸다.
    -   개발자가 예상할 수 있는 없는 값은 null이다.

---

### 변수, 상수

자바스크립트에서 변수를 선언하는 키워드는 두가지가 있다.
var와 let 이다.

```javascript
// JavaScript Code
var a = 5;
let b = "Hello, World!";
let c = "Crack your limits, Crecker!";
var d = true;
let e = [1, 2, 3, 4, 5];
let f = 3.85;
```

var는 ECMA2015(ES6) 이전에 있던 유일한 변수 키워드 였다.
그래서 사실 ES6 이전에는 그냥 모든 변수가 var 였다.

그러나 ECMA2015 이후에는 공식적으로 let과 const(상수 할당 키워드)만을 사용할 것을 권장한다.
따라서 코드상으로 문제가 없다면 let과 const를 쓰자.

위의 코드는 Java의 다음 코드와 같다.

```java
// Java Code
int a = 5;
String b = "Hello, World!";
String c = "Crack you limits, Crecker!";
boolean d = true;
int[] e = [1,2,3,4,5];
double f = 3.85;
```

상수 변수는 다음과 같다.

```javascript
// JavaScript Code
const a = 3;
const b = 1.5;
const c = "Server";
```

이는 Java의 다음 코드와 같다.

```java
// Java Code
final int a = 3;
final double b = 1.5;
final String c = "Server";
```

var와 let이 다른 키워드 인건 알겠는데, 차이가 아예 없을까?
사실 있다.

| 키워드 | 스코프   | 재할당 여부 | 재선언 여부 |
| ------ | -------- | ----------- | ----------- |
| var    | 함수범위 | 가능        | 가능        |
| let    | 블록범위 | 가능        | 불가능      |
| const  | 블록범위 | 불가능      | 불가능      |

스코프는 변수가 효력을 미치는 영역을 얘기하는데, let과 const는 Java에서의 변수의 범위를 생각하면 된다.
그러나 var는 함수범위 스코프인데, 이는 예시를 들어보면 이해가 편하다.

```javascript
let a = 5;
const b = 3;
var c = 1.5;

function Scope(a, b) {
    for (var i = 0; i < 5; i++) {
        let inner = "I'm in loop!";
        console.log(inner);
    }
    console.log(i);
    console.log(inner);
    console.log(a, b, c);
}

Scope(a, b);
var c = 3;
console.log(c);
```

위의 코드를 동작 시켜 보면 다음과 같은 에러가 나온다.

```
VM196:12 Uncaught ReferenceError: inner is not defined
    at Scope (<anonymous>:12:17)
    at <anonymous>:16:1
```

---

### 연산자

연산자는 산술, 대입, 비교 가 있다.

#### 산술 연산자

기본적인 산술 연산자로는 사칙연산자가 있다.

```javascript
let a = 5; // 대입 연산
let b = 8; // 대입 연산

console.log(a + b); // 더하기
console.log(a - b); // 빼기
console.log(a * b); // 곱하기
console.log(a / b); // 나누기 (결과 값은 소수면 소수, 정수면 정수로 나온다)
console.log(a % b); // 나머지연산
console.log(a++); // 1 증가 시키기
console.log(--b); // 1 감소 시키기
```

#### 비교 연산자

자바스크립트에서 비교 연산자는 다음과 같다.

```javascript
let a = 5;
let b = 3;
let c = "5";

console.log(a > b); // 5 > 3 true
console.log(a >= b); // 5 >= 3 true
console.log(a < b); // 5 < 3 false
console.log(a <= b); // 5 <= 3 false
console.log(c > b); // "5" > 3 true
console.log(c >= b); // "5" >= 3 true
console.log(c < b); // "5" < 3  false
console.log(c <= b); // "5" <= 3 false
console.log(a == c); // 5 == "5" true
console.log(a === c); // 5 === "5" false
console.log(a != c); // 5 != "5" false
console.log(a !== c); // 5 !== "5" true
```

주목할 것은 밑에 보이는 ===와 \!\== 이다.
자바스크립트는 같음과 같지않음을 보이는 연산자는 두가지 씩 있다.

== 와 === 이다.

== 는 5와 "5"를 같은 값으로 인식하기 때문에, === 를 써주는 것이 좋다.
!= 와 !==도 마찬가지 이다.

---

### 조건문

Java의 if - else문과 동일하다.

다만 switch - case 문에서 기준 변수가 꼭 Number 가 아니어도 된다.

```javascript
let AppjamTeam = "Crecker";

switch (AppjamTeam) {
    case "Crecker":
        console.log("Crecker");
        break;
    case "Flood":
        console.log("Flood");
        break;
    default:
        console.log("SOPT");
}
```

---

### 반복문

반복문은 다음과 같은 경우들이 있다.

-   while문
-   do - while문
-   기초 for문
-   for ... of 문
-   for ... in 문

#### while 문

java의 while문과 동일하다

#### do - while 문

java의 do - while 문과 동일하다.

#### 기초 for 문

java의 for 문과 동일하다.

```javascript
for (let i = 1; i <= 9; i++) {
    console.log(i);
}
```

#### for ... of 문

배열을 순회할 때 사용되도록 특화된 for문이다.

```javascript
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

for (let i of arr) {
    console.log(i);
}
```

위의 코드는 기초 for문의 결과와 동일하다.

#### for ... in 문

객체를 순회할 때 사용되도록 특화된 for 문이다.

```javascript
let person = { fname: "John", lname: "Doe", age: 25 };

let text = "";
for (let x in person) {
    text += person[x] + " ";
}
```

[코드 출처 : https://www.w3schools.com/jsref/jsref_forin.asp](https://www.w3schools.com/jsref/jsref_forin.asp)

x에는 객체의 키 값인 fname, lname, age 순으로 순회하게 된다.
배열에서 사용시 x에는 인덱스 값이 들어간다. (0, 1, 2, ...)

---

#### 배열 내장함수

배열 자체적으로 내장 되어있는 함수들이 있는데, 잘 쓰면 굉장히 유용하고 좋다.

추후 추가

---

#### 프로토타입과 클래스

추후 추가

---

#### 비구조화 할당

자바스크립트에서 지원하는 방식으로 객체 내부에 있는 변수들의 할당을 좀 더 원활하게 도와준다.

예시로 살펴보자.

```javascript
const req = {
    body: { contents: "hello", idx: 1 },
    decoded: 0,
    test: "This is Test"
};

//getter와 getter2의 결과는 같음

function getter(req) {
    let body = req.body;
    let decoded = req.decoded;
    let test = req.test;

    console.log(body);
    console.log(decoded);
    console.log(test);
}

function getter2(req) {
    // 비구조화 할당 사용
    let { body, decoded, test } = req;

    console.log(body);
    console.log(decoded);
    console.log(test);
}
```

---

#### 함수 표현 방식

함수를 나타내는 방법은 두 가지가 있다.

-   함수 선언식
-   함수 표현식

차이는 코드를 통해 알아보자.

```javascript
function declaration(a, b) {
    // 함수 선언식
    return a + b;
}

const expression = function(a, b) {
    // 함수 표현식
    return a + b;
};
```

위와 아래는 하는 행동은 동일하나 자바스크립트 엔진에서 읽는 호이스팅(hoisting) 때문에
코드에서 실행될 때 차이가 있다.

자세한 것은 추후 추가

또한 함수를 쓰는 방법중에 화살표 함수(Arrow function) 이라는 것이 있다.
ECMA2015부터 생긴 문법으로 이를 사용하면 콜백함수를 알아보기 쉽게 쓸 수 있다.

```javascript
const expression = (a, b) => a + b;

const expression1 = () => console.log("This is Server");

const expression2 = index => console.log(index);

const expression3 = (a, b) => {
    let c = 5;
    return a + b + c;
};
```

화살표 함수는 매개변수의 수에 따라 형태가 달라지고, 함수의 줄 수에 따라서 형태가 달라진다.

기본적인 형태는 다음과 같다.

**(매개변수) => 리턴값**

-   매개변수가 없을 때는 빈 소괄호를 써줘야 된다.
-   매개변수가 1개 일때는 소괄호를 생략할 수 있다.
-   함수의 내용이 한줄 일 때는 화살표 뒤에 바로 쓰면 된다.
-   함수의 내용이 여러줄 일 때는 화살표 뒤에 중괄호를 열고 연산등을 넣을 수 있다.

화살표 함수는 메소드로 사용시에 일반적인 함수와 바인딩 되는 것이 다르나, 이는 추후에 추가하겠다.

---

#### spread와 rest문법

추후 추가
