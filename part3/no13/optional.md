# ?. / ?? 연산자 (optional chaining)

?. optional chaining

object 자료에서 원하는 데이터 꺼내고 싶으면 마침표 찍으면 됩니다.

근데 마침표와 똑같은 역할을 하는 ?. 문법이 있습니다.

```javascript
var user = {
  name: "kim",
  age: 20,
};

console.log(user.name);
console.log(user?.name);
```

용도는 마침표와 똑같은데 정확한 기능은

?. 왼쪽에 있는게 null 혹은 undefined 인 경우 마침표찍지 말고 undefined 남겨주세요~

입니다.

하지만 문법의 기능만 배우면 쓸데가 없습니다. 다음날 다 까먹음

어떤 상황에서 쓰면 좋을지 알아갑시다.

어디다 쓰냐면

"중첩된 object 자료에서 에러없이 안전하게 데이터를 꺼낼 때" 사용하면 됩니다.

일단 중첩된 object 자료가 뭔소리냐면

```javascript
var user = {
  name: "kim",
  age: { value: 20 },
};

console.log(user.age.value);
```

object 안에 object가 들어있는 경우를 말합니다.

이 경우 마침표 몇번 찍어야 안에 깊숙히 들어있는 자료를 출력할 수 있는데

자료를 잘못 찾는 경우 에러가 납니다.

```javascript
var user = {
  name: "kim",
  age: { value: 20 },
};

console.log(user.age1.value1); //에러남 ㅅㄱ
```

왜냐면 undefined, null 같은 것에다가 점찍으면 에러가 나서 그렇습니다.

근데 개발시 에러가 나는건 좋은겁니다. 내가 뭘 잘못했는지 찾아 수정할 수 있으니까요.

근데 실제 사이트라면 에러가 나면 큰일인데

에러가 난 부분 하단에 있는 코드들은 실행이 되지 않으니까 사이트가 이상하게 동작할 수 있습니다.

그걸 방지하고 싶으면 .age1 이게 있으면 .value1 해달라고 if 문법 쓰거나 그러면 됩니다.

```javascript
var user = {
  name: "kim",
  age: { value: 20 },
};

console.log(user.age1?.value1); //에러는 안남 매우안전
```

if 쓰기 귀찮으면 ?. 쓰면 됩니다.

"왼쪽에 있는게 null, undefined면 마침표찍지말고 undefined를 남겨주세요" 라는 뜻이라 에러가 나지 않습니다.

```javascript
var user = {
  name: "kim",
};

console.log(user?.name1);
```

Q. 그럼 중첩된 object 말고 간단한 object 자료에서 데이터 뽑을 때도 ?. 쓰면 좋겠네요?

A. 원래 object에서 데이터뽑을 때 해당하는 자료가 없으면 자동으로 undefined가 남아서 그럴 필요 없습니다.

근데 중첩된 object는 마침표를 2번 이상 찍습니다.

그런 경우 undefined에다가도 마침표를 찍을 수 있기 때문에 (에러 위험)

?. 쓰면 안전할 수 있습니다.

(참고) 오해하면 안되는게 ?. 이건 에러를 해결해주는 문법이 아니라 에러나지 않게 감추는 문법일 뿐입니다.

?? nullish coalescing operator

```javascript
var user;

console.log(user ?? "로딩중");
```

?? 왼쪽이 null, undefined 일 경우 오른쪽 보여달라는 뜻입니다.

이것도 비슷한 용도를 가지고 있는데

예를 들어 var user라는 변수를 유저에게 보여줘야한다고 합시다.

그래서 html안에 보여달라고 코드짜놨는데

근데 var user가 ajax 요청 등 때문에 늦게 도착하면 어떻게 합니까?

유저가 undefined 이런걸 볼 수도 있겠군요.

그게 싫다면 user 안에 뭐가 들어있으면 html에 보여주세요~ 라고 if문을 쓰거나 그러면 되는데

그게 귀찮으면 변수 우측에 ?? 붙이면 됩니다.

user ?? '대신보여줄문자'

이러면 user 라는 변수에 아직 뭐가 없으면 오른쪽에 있는 문자를 대신 보여줍니다.

특히 React, Vue 이런거 하다보면 데이터 늦게 도착하는게 일상인데

그런 라이브러리 쓸 때 좀 유용한 문법입니다.
