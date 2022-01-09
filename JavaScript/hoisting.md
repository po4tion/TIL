# Hoisting

> 호이스팅은 인터프리터가 변수와 함수의 메모리 공간을 선언하기 전에 미리 할당하는 것을 의미합니다.

---

JavaScript는 초기화를 제외한 선언만 호이스팅합니다. `var` 키워드로 선언한 변수의 경우 호이스팅 시 `undefined`로 변수를 초기화합니다. `let`과 `const`로 선언한 변수도 호이스팅의 대상이지만 `undefined`로 초기화하지는 않고 예외가 발생합니다.

```javascript
console.log(value); // undefined

var value; // 선언
value = 12; // 초기화
```

```javascript
hoist();

function hoist() {
 console.log('첫번째 : ', value); // undefined

 var value = 28;

 console.log('두번째 : ', value); // 28
}
```

```javascript
// 선언시에는 함수가 아닌 undefined이므로 TypeError 예외가 발생합니다.
hoist();

var hoist = function () {
 console.log('첫번째 : ', value); // TypeError: hoist is not a function

 var value = 28;

 console.log('두번째 : ', value);
};
```

```javascript
// const 또는 let 선언시에는 예외가 발생합니다.
console.log(hoist); // ReferenceError: Cannot access 'hoist' before initialization

const hoist = 128;
```

## 정리

호이스팅은 변수의 선언과 초기화를 분리한 후, 선언만 코드의 최상단으로 옮기는 것입니다. ( =선언이 초기화보다 먼저 메모리에 저장되어 있습니다.)
