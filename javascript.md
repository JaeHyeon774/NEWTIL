<h1>Java Script</h1>

## emmet

---

* html, css등을 작성할 때, 시간을 단축시켜주는 확장기능!
* emmet플러그인만 설치되어 있다면 사용가능!!

####  기본문법

* **`div>ul>li`**

  ```html
  <div>
      <ul>
          <li></li>
      </ul>
  </div>
  ```

* **`div+p+bq`**

  ```html
  <div></div>
  <p></p>
  <blockquote></blockquote>
  ```

* **`ul>li*5`**

  ```html
  <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
  </ul>
  ```

* **`ul>li.item$*5`** or **`ul>li#item$*5`**

  ```html
  <ul>
      <li class="item1"></li>
      <li class="item2"></li>
      <li class="item3"></li>
      <li class="item4"></li>
      <li class="item5"></li>
  </ul>
  ```

* `div+div>p>span+em^bq`

  ```html
  <div></div>
  <div>
      <p>
          <span></span>
          <em></em>
      </p>
      <blockquote></blockquote>
  </div>
  ```

* `div+div>span>p>span+em^^bq`

  ```html
  <div></div>
  <div>
      <span>
          <p><span></span><em></em></p>
      </span>
      <blockquote></blockquote>
  </div>
  ```

  

## javascript 실행순서(A->C->B)

```javascript
<script>
    alert('A');
	setTimeout(function() {
        alert('B');
    },0);
	alert('C');
</script>
```



