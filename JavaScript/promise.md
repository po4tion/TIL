# Promise

> Promise를 사용하면 비동기 메서드에서 마치 동기 메서드처럼 값을 반환할 수 있습니다. 다만 최종 결과를 반환하는 것이 아니고, 미래의 어떤 시점에 결과를 제공하겠다는 약속을 반환합니다.

---

## Promise의 상태

### 대기(pending)

```javascript
new Promise();
```

아직 약속을 수행중인 상태(fulfilled 혹은 reject 되지 않은 초기 상태)입니다.

### 이행(fulfilled)

```javascript
new Promise((resolve, reject) => {
 resolve();
});
```

`resolve` 메소드가 호출되면 이행 상태가 됩니다. 이행 상태는 약속이 완료된 상태입니다.

### 거부(rejected)

```javascript
new Promise((resolve, reject) => {
 reject();
});
```

`reject` 메소드가 호출되면 거부 상태가 됩니다. 거부 상태는 약속이 실패한 상태입니다.

## 예시

```javascript
let myFirstPromise = new Promise((resolve, reject) => {
 setTimeout(function () {
  resolve('성공!');
 }, 250);
});

myFirstPromise.then((successMessage) => {
 console.log('와! ' + successMessage); // 와! 성공!
});
```

## 출처

[MDN Web Docs](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
[Poiemaweb](https://poiemaweb.com/es6-promise)
