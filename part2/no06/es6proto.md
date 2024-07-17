# 객체지향4. ES6방식으로 안쉽게 구현하는 상속기능 (class)

```javascript
class 부모 {
  constructor() {
    this.name = "Kim";
    this.sayHi = function () {
      console.log("hello");
    };
  }
  sayHi() {
    console.log("hello");
  }
}

var 자식 = new 부모();
Object.getPrototypeOf(자식);
```
