# Web Components : 커스텀 HTML 태그 만들기

```html
<custom-input></custom-input>
```

```javascript
class 클래스 extends HTMLElement {

   connectedCallback() {
      let name = this.getAttribute('name');
      this.innerHTML = '<label>${name}을 입력하쇼</label><input>'
   }

   static get observedAttributes() {
       return ['name']
   }
   attributeChangedCallback() {
       (attribute 변경시 실행할 코드)
   }
}

customElements.define("custom-input", 클래스);
```
