# shadow DOM과 template으로 HTML 모듈화하기

```html
<custom-input></custom-input>

<template id="template1">
  <label>이메일을 입력하쇼</label><input />
  <style>
    label {
      color: red;
    }
  </style>
</template>

<script>
  class 클래스 extends HTMLElement {
    connectedCallback() {
      this.attachShadow({ mode: "open" });
      this.shadowRoot.append(template1.content.cloneNode(true));
      let el = this.shadowRoot.querySelector("label");
      el.addEventListener("click", function () {
        console.log("클릭함");
      });
    }
  }
  customElements.define("custom-input", 클래스);
</script>
```
