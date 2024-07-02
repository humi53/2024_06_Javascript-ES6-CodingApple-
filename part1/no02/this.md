# this 키워드를 알아보자 2. event listener와 constructor

### this의 3,4번째 뜻

- 새로 생성되는 오브젝트
  - constructor 안에서

```javascript
function 기계() {
  this.이름 = "Kim";
}
var 오브젝트 = new 기계();
```

- e.currentTarget
  - 이벤트 리스터 안에서

```javascript
document.getElementById("버튼").addEventListener("click", function (e) {
  console.log(this);
});
```

### 생각.

- 콜백함수는 왜 window를 가르킬까
  - 생성해서 가져다 붙이는 함수라.. 근본이 없음. 일반함수와 같게 처리.
- arrow function
  - this는 내 위의 값을 그대로 물려받아서 사용하겠음.
  - 그래서 애로우 함수를 사용하게 되면 this값이 달라져 기존방식으로 쓸수 없다.
