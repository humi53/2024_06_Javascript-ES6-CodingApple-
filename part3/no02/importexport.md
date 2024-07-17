# import / export 를 이용한 파일간 모듈식 개발

(1) export default / import 를 쓰면

다른 파일에 있는 변수 등을 가져다쓸 수 있습니다.

변수 함수 class 전부 가능합니다.

(library.js)

var a = 10;
export default a;

---

(index.html)

<script type="module">
  import a from 'library.js';
  console.log(a);
</script>

JS 파일에서는 특정 변수를 다른 파일에서 이용할 수 있게 내보내고 싶으면

export default 변수명 이라고 하시면 됩니다.

그리고 그 변수를 가져다쓰고 싶다면

다른 파일에서 import 어쩌구 from '경로'

해주시면 됩니다.

(import시 어쩌구라는 변수명은 여러분 아무렇게나 작명이 가능합니다.)

(2) 여러개를 export 할 수도 있습니다

JS파일에서 변수를 여러개 만들고 그걸 다 내보내고싶으면

export 라는 키워드를 여러번 쓰시면 됩니다.

(library.js)

var a = 10;
var b = 20;
export {a, b};

---

(index.html)

<script type="module">
  import {a,b} from 'library.js';
  console.log(a);
</script>

근데 export 라고 쓰실 땐

export {변수명1, 변수명2 ...} 이렇게 담아주셔야합니다.

혹은 export var a = 10; 이렇게 쓰셔도 됩니다.

export 키워드로 내보낸 것들을 import 하실 땐

import {변수명1, 변수명2 ...} from '경로' 이렇게 가져오셔야합니다.

export default와 차이점은..

(3) 그럼 export와 export default 동시에 사용하면?

그래도 잘 됩니다.

근데 import할 때 어떻게 해야할지 감이 안오죠?

(library.js)

var a = 10;
var b = 20;
var c = 30;
export {a, b};
export default c;

---

(index.html)

<script type="module">
  import c, {a,b} from 'library.js';
  console.log(c);
</script>

이렇게 import 해오시면 됩니다.

export default 한건 맨 왼쪽에 써주시면 되고

그 다음부터 이제 {} 중괄호 안에 export 했던 변수들을 적어주시면 됩니다.

(4) 변수명이 마음에 안들면 as로 새로 짓자

import를 쓸 때 변수명 오른쪽에 as라는 키워드를 붙일 수 있습니다.

변수명 as 새변수명 이렇게 하면 import하는 변수의 변수명을 멋있는걸로 바꿀 수 있습니다.

(library.js)

var a = 10;
var c = 30;
export {a};
export default c;

---

(index.html)

<script type="module">
  import c, {a as 폭발} from 'library.js';
  console.log(폭발);
</script>

a라는 것은 폭발로 이름을 바꿔봤습니다.

(5) import할 때 변수들이 너무 많으면 \* 기호를 씁시다

export { } 했던 변수들이 100개면

import 오른쪽에 변수를 100개나 쭉 써줘야합니까?

맞습니다 ㄷㄷ

근데 그러기 싫으시면 변수들을 한꺼번에 object에 담아서 import 해올 수 있습니다.

(library.js)

var a = 10;
var b = 20;
var c = 30;
export {a,b};
export default c;

---

(index.html)

<script type="module">
  import c, * as 변수모음 from 'library.js';
  console.log(변수모음.a);
  console.log(c);
</script>

- 이라는 기호는 export { } 했던 애들을 그냥 다 import 해주세요~ 라는 뜻입니다.

근데 그냥 쓰면 안되고 as로 별명을 꼭 지어주어야합니다.

그럼 이제 별명에 export { } 했던 변수들이 다 들어갑니다.

(export default 했던건 그냥 원래대로 import 하시면 되고요)

옛날엔 require, module.exports 라는게 있었습니다.

옛날에 Require.js 이상한 라이브러리를 쓰거나 nodejs 개발시

자바스크립트를 모듈식으로 개발이 가능했었습니다.

이렇게 씁니다.

(export 하는 js파일)

module.exports.a = 10 ;

---

(import 하는 js파일)

var 가져온거 = require('/library.js');
이러면 a를 쓸 수 있었습니다.

근데 이제는 ES6 import/export를 쓰면 되기 때문에

아 그냥 저런게 있었구나 라고 이해만 하셔도 되겠습니다.

나중에 저런 옛날 코드를 해석할 일이 있으면 그 때 찾아보셔도 충분하니까요.

그리고 import/export는 당연 IE 호환성이 없기 때문에

단순한 html css js 프론트엔드 개발시 JS파일을 HTML에 첨부하시려면

<script src="경로"></script> 이걸 쓰도록 합시다. 이것이 원조 import 문법 아니겠습니까.

혹은 모던 브라우저에선 <script type="module" src="경로"></script> 이렇게 하면 import export 문법이 사용가능해지는데

대부분은 리액트 뷰 nodejs 이런거할 때 많이 사용하게 됩니다.
