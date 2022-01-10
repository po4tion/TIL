# Arrow Function

---

## 화살표 함수의 제한점

1. `this`나 `super`에 대한 바인딩이 없고 메소드로 사용될 수 없습니다.
2. bind, apply, call 메소드를 사용할 수 없습니다.
3. 생성자로 사용할 수 없습니다.

```javascript
function foo() {
 console.log('bar');
}

foo(); // bar
```

```javascript
const foo = () => {
 console.log('bar');
};

foo(); // bar
```

## 참고사항

[this에서의 화살표 함수](https://github.com/po4tion/TIL/blob/main/JavaScript/this.md#%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98-%ED%98%B8%EC%B6%9C)

## 출처

[MDN Web Docs](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
