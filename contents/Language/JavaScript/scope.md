# 스코프(Scope)

###### content

- [Scope란?]()
- [전역 스코프(Global scope)]()
- [함수 레벨 스코프(Function-level scope)]()

---

<br />

## 스코프란?

<br />

스코프는 참조 대상 식별자를 찾아내기 위한 규칙

자바스크립트는 이 규칙대로 식별자를 찾는다 !

```jsx
var x = "globalScope";

function foo() {
  var x = "functionScope";
  console.log(x);
}

foo(); // ?
console.log(x); // ?
```

위 예제에서 전역에 선언된 변수 `x`는 어디에든 참조할 수 있다.

하지만 함수 `foo()` 내에서 선언된 변수 `x` 는 함수 `foo()` 내부에서만 참조할 수 있고, 함수 외부에서는 참조할 수 없다.

이러한 규칙을 **스코프**라고 한다.

<aside>
❓ 만약 스코프가 없다면 어떻게 될까?
<br />
스코프가 없다면 같은 식별자 이름은 충돌을 일으키므로 프로그램 전체에서 하나밖에 사용할 수 없다.
<br />
디렉터리가 없는 컴퓨터를 생각해보자. 디렉터리가 없다면 같은 이름을 갖는 파일을 하나밖에 만들 수 없다.
<br />
이와같이 식별자 이름의 충돌을 방지한다.

> **전역 스코프(Global scope)**<br />
> 코드 어디에서든지 참조할 수 있다.<br /> <br />
> **지역 스코프(Local scope / Function-level scope)**<br />
> 함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다.<br /><br />
> **전역 변수(Global variable)**<br />
> 전역에서 선언된 변수이며 어디에든 참조할 수 있다.<br /><br />
> **지역 변수(Local variable)**<br />
> 지역(함수) 내에서 선언된 변수이며 그 지역과 그 지역의 하부 지역에서만 참조할 수 있다.

변수는 **선언 위치**에 의해 스코프를 가지게 된다.<br />
즉, 전역에서 선언된 변수는 전역 스코프를 갖는 전역 변수이고,<br />
지역에서 선언된 변수는 지역 스코프를 갖는 지역 변수가 된다.
<br /><br />
진역 스코프를 갖는 전역 변수는 코드 어디서든지(전역) 참조할 수 있다.<br />
함수 내부(지역)에서 선언된 지역 변수는 그 지역과 그 지역의 하부 지역에서만 참조할 수 있다.

<details>
<summary>Q. 그렇다면 위 코드에서 `foo()` 와 `console.log(x)` 는 각각 무엇을 출력하게 될까?</summary>
    
    `foo()` ⇒ functionScope
    
    `console.log(x)` ⇒ globalScope
</details>
<br />

<br />

##### [🔼 목차로 이동]()

---

<br />

## 전역 스코프(Global scope)

<br />

```jsx
var global = "global";

function foo() {
  var local = "local";
  console.log(global);
  console.log(local);
}
foo();

console.log(global);
console.log(local); // Uncaught ReferenceError: local is not defined
```

변수 `global` 은 함수 영역 밖의 전역에서 선언되었다.<br />
자바스크립트는 타 언어와는 달리 특별한 시작점(Entry point)이 없어서 위 코드와 같이 전역에 변수나 함수를 선언하기 쉽다.<br /><br />
따라서 전역에 변수를 선언하기 쉬우며 이것은 전역 변수를 남발하게 하는 문제를 야기시킨다.<br /><br />
전역 변수의 사용은 **변수 이름이 중복**될 수 있고,<br />
**의도치 않은 재할당에 의한 상태 변화로 코드를 예측하기 어렵게 만드므로 사용을 억제하여야 한다.**
<br />

<br />

##### [🔼 목차로 이동]()

---

<br />

## 함수 레벨 스코프(Function-level scope)

<br />

###

```jsx
var a = 10; // 전역변수

(function () {
  var b = 20; // 지역변수
})();

console.log(a); // 10
console.log(b); // "b" is not defined
```

자바스크립트는 함수 레벨 스코프를 사용한다.<br />
함수 내에서 선언된 매개변수와 변수는 함수 외부에서는 유요하지 않는다.<br />
내부 함수는 자신을 포함하고 있는 외부함수의 변수에 접근할 수 있다.

```jsx
var x = "global";

function foo() {
  var x = "local";
  console.log(x); // 1번

  function bar() {
    console.log(x); // 2번
  }

  bar();
}
foo();
console.log(x); // 3번
```

<details>
<summary>다음 코드에서 1번, 2번, 3번에 찍히는 글자는?
</summary>
    
    1번: `local`
    
    2번: `local`
    
    3번: `global`
</details>
