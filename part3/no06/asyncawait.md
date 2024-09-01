# Promise 어려워서 싫으면 async/await을사용합시다

- async
- await
- try/catch

- 프로미스를 이런식으로 사용하지만

```javascript
ajaxloding.then((e) => {
  console.log(e);
});
```

- await은 기다려주세요 임.
- async await을 사용하면

```javascript
async function add() {
  var result = await ajaxloding;
  console.log(result);
}
add();
```

- async는 프로미스를 간편하게 사용하게 하지만 실패는 처리 안해줌.
- await에서 애러가나면 페이지가 멈추게 됨, 그래서 try catch를 같이 사용해야됨.
