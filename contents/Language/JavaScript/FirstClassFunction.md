# 일급함수와 일급객체

###### content

- [일급함수]()
  - 변수에 함수 할당
  - 함수를 인자로 전달
  - 함수 반환
- [일급객체]()
  - 세부 카테고리 소제목2-1
  - 세부 카테고리 소제목2-2
    <br>
    <br>
    <br>

---

<br />

## 일급 함수 (First-Class Function)

<br />

함수를 다른 변수와 동일하게 다루는 언어를 **일급 함수**를 가졌다고 표현

- 변수에 함수 할당

  ```js
  const foo = function () {
    console.log("foobar");
  };

  // 변수를 사용해 호출
  foo();
  ```

  익명 함수를 변수에 할당한 다음, 그 변수를 사용하여 끝에 괄호를 추가하여 함수를 호출

  > 함수가 이름을 가지고있더라도 할당한 변수 이름을 사용해 함수를 호출 가능
  > 이름을 지정하면 코드를 디버깅 할 때 유용하지만
  > 호출하는 방식에는 영향을 미치지 않는다.

  <br />

- 함수를 인자로 전달

  ```js
  function sayHello() {
    return "Hello, ";
  }
  function greeting(helloMessage, name) {
    console.log(helloMessage() + name);
  }

  // `sayHello`를 `greeting` 함수에 인자로 전달
  greeting(sayHello, "JavaScript!");
  ```

  `sayHello()` 함수를 `greeting()` 함수의 인자로 전달

  함수를 어떻게 변수처럼 다루는지 보여주는 예시

  > 다른 함수에 인자로 전달된 함수를 **콜백 함수** 라고 함
  > `sayHello` 는 콜백 함수

  <br />

- 함수 반환
  ```js
  function sayHello() {
    return function () {
      console.log("Hello!");
    };
  }
  ```
  함수가 함수를 반환
  JavaScript 에서는 함수를 변수처럼 취급하기 때문에 함수를 반환할 수 있음
  > 함수를 반환하는 함수를 **고차함수**라고 부른다.

<br />

##### [🔼 목차로 이동]()

---

<br />

## 일급시민 (First-Class Citizen)

<br />

```js
val = 1;
```

1은 변수의 값이 될 수 있나 ? Yes !

→ 숫자는 1급 시민이다 !

```jsx
val = if(🐑) {
	🐎;
}
```

조건문은 변수의 값이 될 수 있나 ? No !

→ 조건문은 1급 시민이 될 수 없다.

<br />

```js
val = function(🐑) {
	return 🐎
}
```

JavaScript에서의 함수는 값이 될 수 있다.

→ 함수는 1급 시민이다 !

<br />

**1급시민의 조건**

1. 변수(variable)에 담을 수 있다.

   ```js
   const variable = 1;
   ```

<br />
1. 인자(parameter)로 전달할 수 있다.

```js
val = function(🐑){
	return 🐎
}
fn(val)
```

<br />
1. 반환 값(return value)으로 전달할 수 있다.

```js
function fn(){
	val = function(🐑){
		return 🐎
	}
	return val;
}
```

<br />

##### [🔼 목차로 이동]()

---

<br />

## 1급 객체 (First-Class Object)

<br />

자바스크립트의 함수는 **일급 객체**이다.

1급 객체는 1급 시민의 조건을 충족하는 객체

JavaScript에서 객체는 1급 시민이다. 따라서, 1급 객체이다.

다음과 같은 조건을 만족하는 객체를 **일급 객체**라 한다.

1. 무명의 리터럴로 생성할 수 있다. 즉, 런타임에 생성이 가능하다.
2. 변수나 자료구조(객체, 배열 등)에 저장할 수 있다.
3. 함수의 매개변수에 전달할 수 있다.
4. 함수의 반환값으로 사용할 수 있다.

자바스크립트의 함수는 다음 예제와 같이 위의 조건을 모두 만족하므로 일급 객체다.

```js
// 1. 함수는 무명의 리터럴로 생성할 수 있다.
// 2. 함수는 변수에 저장할 수 있다.
// 런타임(할당 단계)에 함수 리터럴이 평가되어 함수 객체가 생성되고 변수에 할당된다.
const increase = function (num) {
	return ++num;
};

const decrease = function (num) {
	return --num;

// 2. 함수는 객체에 저장할 수 있다.
const auxs = { increase, decrease };
```

```js
// 3. 함수의 매개변수에 전달할 수 있다.
// 4. 함수의 반환값으로 사용할 수 있다.
function makeCounter(aux) {
  let num = 0;

  return function () {
    num = aux(num);
    return num;
  };
}

// 3. 함수는 매개변수에게 함수를 전달할 수 있다.
const increaser = makeCounter(auxs.increase);
console.log(increaser()); // 1
console.log(increaser()); // 2

const decreaser = makeCounter(auxs.decrease);
console.log(descrease()); // -1
console.log(descrease()); // -2
```

함수가 일급 객체라는 것은 함수를 객체와 동일하게 사용할 수 있다는 의미

객체는 값이므로 함수는 값과 동일하게 취급

따라서 함수는 값을 사용할 수 있는 곳

(변수 할당문, 객체의 프로퍼티 값, 배열의 요소, 함수 호출의 인수, 함수 반환문)

이라면 어디서든지 리터럴로 정의할 수 있으며 런타임에 함수 객체로 평가

일급 객체로서 함수가 가지는 가장 큰 특징은 일반 객체와 같이 함수의 매개변수에 전달할 수 있으며,

함수의반환값으로 사용할 수도 있다는 것

이는 함수형 프로그래밍을 가능케 하는 자바스크립트의 장점 중 하나

함수는 객체이지만 일반 객체와는 차이가 있음.

일반 객체는 호출할 수 없지만 함수 객체는 호출할 수 없음.

그리고 함수 객체는 일반 객체에는 없는 함수 고유의 프로퍼티를 소유
<br />

### Reference

[🔗 MDN](https://developer.mozilla.org/ko/docs/Glossary/First-class_Function)

[🔗 생활코딩](https://www.youtube.com/watch?v=TAyLeIj1hMc)

[🔗 개발을해보자](https://bbbyung2.tistory.com/46)

🔗 모던 자바스크립트 Deep Dive : 18.1 일급 객체
<br>
<br>
<br>

##### [🔼 목차로 이동](#)
