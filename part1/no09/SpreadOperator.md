# 모든 괄호를 없애주는 Spread Operator 활용방법 1

`...변수`

- 대괄호 제거

- 문자열 펼쳐줌

- 배열이나 객체를 복사해서 생성.

- array를 파라미터로 쪼개서 집어넣기

  - 예전 : `더하기.apply(undefined, 어레이);`
  - 지금 : `더하기(...어레이);`

- call 과 apply 차이
  - apply는 뒤에 어레이가 붙고 call은 파라미터를 쪼개서 넣는다.

```javascript
var person = {
  인사: function () {
    console.log(this.name + "안녕");
  },
};
var person2 = {
  name: "손흥민",
};

person.인사();
person.인사.apply(person2, [1, 2]);
person.인사.call(person2, 1, 2);
```

11 분☀️
Spread Operator 활용방법 2 & apply, call 함수 알아보기

0:00 활용방법 3. 어레이를 풀어헤쳐서 함수 파라미터로 집어넣기

4:20 apply, call 함수 개념

Spread operator 나머지 활용방법을 알아봅시다.

이걸 어디에 쓰냐면 3. array를 파라미터형태로 집어넣고 싶을 때 씁니다.

뭔소리냐면 일단 예시를 들기 위해 함수를 하나 만들어봅시다.

function 더하기(a,b,c){
console.log(a + b + c)
}
더하기(1,2,3);
파라미터를 3개 받아와서 전부 더해주는 더하기라는 함수를 만들어봤습니다.

그런데 여기 파라미터를 집어넣을 때

직접 1,2,3이라고 작성해서 넣는게 아니라

이미 존재하는 array에 있던 내부 자료들을 쏙 집어넣고 싶으면 어떻게하나요?

그니까 예를 들면...

function 더하기(a,b,c){
console.log(a + b + c)
}

var 어레이 = [10, 20, 30];
어레이라는 자료 안에 있는 모든 숫자 10,20,30을 더하기() 함수의 파라미터로 집어넣으려면 어떻게 해야합니까.

더하기(10,20,30);
이렇게 직접 손으로 적거나

더하기(어레이[0], 어레이[1], 어레이[2]);
이렇게 하거나 해야겠죠?

근데 그게 귀찮으시면 spread 연산자를 쓰시면 됩니다.

function 더하기(a,b,c){
console.log(a + b + c)
}

var 어레이 = [10, 20, 30];
더하기(...어레이);
그러면 출력했을 때 10, 20, 30을 더해준 결과가 잘 출력됩니다.

▼ spread 연산자가 없던 시절엔 이런 식으로 작성했었습니다.

function 더하기(a,b,c){
console.log(a + b + c)
}

var 어레이 = [10, 20, 30];
더하기(...어레이); //요즘방식
더하기.apply(undefined, 어레이); //옛날방식
apply라는 이상한 함수를 뒤에 붙여서 실행을 했었는데 이게 뭔지 자세히 알아보도록 합시다.

왜냐면 여러분 나중에 객체지향 문법같은거 배우실 때 가끔 등장하는 함수들이니까요.

apply, call 함수가 뭔지 알아보자

일단 예시를 들기 위해 오브젝트를 두개 만들어봅시다.

var person = {
인사 : function(){
console.log(this.name + '안녕')
}
}

var person2 = {
name : '손흥민'
}
person이라는 오브젝트에는 멋진 인사라는 함수를 만들어 넣었고

person2는 보잘것없이 그냥 name : '손흥민' 이라는 자료만 넣었습니다.

그런데 person에 만들어놓은 멋진 person.인사()라는 함수를 person2에서도 쓰고 싶습니다.

그럼 어떻게 해야할까요?

person2에다가 직접 인사()라는 함수를 코딩해서 집어넣으면 되겠죠?

근데 그게 불가능한 경우가 가끔 있습니다. (혹은 귀찮거나)

그럴 때 apply를 쓰시면 됩니다.

apply는 이 함수를 실행하는데.. 저기 오브젝트에다가 적용해서 실행해주세요~ 라는 뜻입니다.

그래서 한번 시도해봅시다.

var person = {
인사 : function(){
console.log(this.name + '안녕')
}
}

var person2 = {
name : '손흥민'
}

person.인사.apply(person2);
▲ 맨 마지막줄에 적은 코드가 뭔 의미냐면

person.인사()라는 함수를 쓰는데 person2라는 오브젝트에 적용해서 실행해라~

또는 person.인사()라는 함수를 쓰는데 person2라는 오브젝트에 있는 함수처럼 실행해라~ 라는 뜻입니다.

apply 함수의 사용법은

실행할함수.apply(적용할곳);

이라고 보시면 됩니다.

이제 apply만 기억해주시면 여러가지 유용한 함수들을 내가 원하는 곳에 붙여서 쉽게 실행가능합니다.

근데 이거랑 아주 똑같은 기능을 하는 함수가 하나 더 있습니다. call 이라고 있어얌

var person = {
인사 : function(){
console.log(this.name + '안녕')
}
}

var person2 = {
name : '손흥민'
}

person.인사.apply(person2);
person.인사.call(person2);
▲ apply와 call은 실행 결과도 똑같고 사용법도 똑같습니다.

하지만 차이점이 하나 있는데, 내가 person.인사()에 파라미터를 넣어서 실행하고 싶은 경우에는

person.인사.apply(person2, 파라미터);
person.인사.call(person2, 파라미터);

이렇게 실행하셔야하는데

이 때 apply는 파라미터를 [array]로 한꺼번에 집어넣을 수 있고

call은 그냥 1,2,3 이렇게 일반 함수처럼 만 집어넣을 수 있습니다.

var person = {
인사 : function(){
console.log(this.name + '안녕')
}
}

var person2 = {
name : '손흥민'
}

person.인사.apply(person2, [1,2,3]);
person.인사.call(person2, 1,2,3);
▲ 파라미터 집어넣는 방법만 좀 차이가 있지 아무튼 call, apply의 실행내용은 똑같습니다.

apply함수는 저렇게 어레이 내의 데이터를 파라미터로 한꺼번에 집어넣을 수 있다는 유용한 기능을 제공하기 때문에

옛날 고대의 개발자들이 파라미터가 많은 함수를 만들 때 자주 사용했습니다.

그럼 이제 아까 함수에 array 집어넣는 예제가 이해가 가기 시작합니다.

```javascript
function 더하기(a, b, c) {
  console.log(a + b + c);
}

var 어레이 = [10, 20, 30];
더하기(...어레이); //요즘방식 넣기
더하기.apply(undefined, 어레이); //옛날방식 넣기
```

이제 이거 옛날방식인

`더하기.apply(undefined, 어레이)`
가 무슨 뜻인지 아시겠습니까.

더하기() 함수를 실행하는데 undefined에 적용해서 실행해주시고요 파라미터로 어레이를 집어넣어주세요~ 라는 뜻입니다.

이러면 편법같은 느낌이 들지만 array를 풀어헤쳐서 파라미터로 집어넣으실 수 있습니다.

Q. 잉 근데 undefined에 적용하는건 뭔소리인가요?

A. 실은 그냥 아무곳에도 적용해서 실행하지 않게하기 위해 적은 내용입니다. 그냥 쌩으로 더하기() 함수가 실행됩니다.

왜냐면 더하기()함수는 어디에도 적용할 필요가 없으니까요. 근데 비워두면 문제가 생기기 때문에 아무 값이나 집어넣은 것입니다.

결론은 spread 연산자가 생긴게 다행입니다
