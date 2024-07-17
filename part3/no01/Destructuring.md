# 틀린그림 찾기능력이 향상되는 Destructuring 문법

```javascript
var name = "Kim";
var age = 30;

var obj = { name: name, age: age };
```

```javascript
function 함수(name, age) {
  console.log(name);
  console.log(age);
}

var array = ["Kim", 30];
함수(array[0], array[1]);

function 함수([name, age]) {
  console.log(name);
  console.log(age);
}

var array = ["Kim", 30];
함수(["Kim", 30]);
```
