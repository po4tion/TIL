# Closure

> MDN 문서에서 클로저는 함수와 함수가 선언된 어취적 환경의 조합이라고 설명합니다.

---

```javascript
function closure() {
 const value = 128;

 const closureFunc = () => console.log(value);

 return closureFunc;
}

const result = closure();

result(); // 128
```

위의 코드에서 `closure()`는 result에 `closureFunc`를 반환하고 콜스택에서 제거되었으므로 value 값 또한 유효하지 않게 됩니다. 하지만 신기하게도 `result()`를 실행해보면 128이 출력됩니다.

이처럼 클로저는 반환된 내부함수가 자신이 선언됐을 때의 환경(Lexical environment)을 기억하여 선언되었던 환경 밖에서 호출되어도 그 환경에 접근할 수 있는 함수를 말합니다.

즉, 클로저는 자신이 생성될 때의 환경을 기억하는 함수입니다.

```javascript
function wrong() {
 for (var i = 0; i < 5; i++) {
  setTimeout(function () {
   console.log(i);
  }, 100);
 }
}

wrong();

/* 
  5
  5
  5
  5
  5
*/
```

위 코드는 100ms 마다 `i`값을 출력하도록 설계되었지만 실제로는 `5`만 잔뜩 출력됩니다. 클로저를 보다 더 잘 이해하기 위해서는 lexical scoping에 대해 이해하셔야 합니다.

```javascript
function test() {
 for (var i = 0; i < 5; i++) {
  setTimeout(function () {
   // test
  }, 100);
 }
 console.log(i);
}

test(); // 5
```

`var`은 함수 스코프로 `wrong()` 안에서 선언된 `console.log(i)`는 `for`문을 벗어나는 조건인 5를 값으로 가집니다. `setTimeout()`이 실행되기 전 이미 반복이 끝난 반복문에 의해 함수 스코프를 가진 `i`는 5 값을 잔뜩 출력하는 것입니다.

```javascript
function test() {
 for (var i = 0; i < 5; i++) {
  (function (k) {
   setTimeout(function () {
    console.log(k);
   }, 100);
  })(i);
 }
}

test();
/* 
  0
  1
  2
  3
  4
*/
```

위 코드는 클로저를 활용하여 반복문이 한바퀴씩 돌때마다 새로운 스코프를 생성해주어 문제를 해결했습니다.

- 번외(let 활용)
  > let은 블록 스코프로 클로저를 활용하지 않아도 반복문이 반복할 때 마다 새로운 스코프를 생성하여 문제를 해결합니다.

```javascript
function test() {
 for (let i = 0; i < 5; i++) {
  setTimeout(function () {
   console.log(i);
  });
 }
}

test();
/* 
  0
  1
  2
  3
  4
*/
```

## 출처

[MDN Web Docs](https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures)  
[PoiemaWeb](https://poiemaweb.com/js-closure)
