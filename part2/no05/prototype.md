# 객체지향2. 이거 보고 prototype 이해 못하면 강의 접습니다

# 객체지향3. prototype의 특징 몇가지

- `__proto__`
- `prototype`

```javascript
var 부모 = { name: "Kim" };
var 자식 = {};

자식.__proto__ = 부모;
console.log(자식.name);
```
