# (간만에 쉬운거) ES5방식으로 쉽게 구현하는 상속기능

```javascript
var 부모 = { name: "Kim", age: 50 };
var 자식 = Object.create(부모);
자식.age = 20;

var 손자 = Object.create(자식);

console.log(손자.age);
```
