## HTML

---

* HTML의 구조

  ```html
  <html>
      <head>
          <title>Page title</title>
      </head>
      <body>
          <h1>This is a heading</h1>
          <p>This is a paragraph.</p>
          <p>This is another paragraph.</p>
      </body>
  </html>
  ```

* Headings

  * `<h1>` ~ `<h6>`까지 있음.
  * h1에 가장 중요한것을 작성 숫자가 작을 수록 중요도는 DOWN 크기 또한 DOWN

* Paragraph

  * `<p>`은 문단을 나타니며, 브라우저는 문단의 앞, 뒤에 자동으로 빈줄을 추가한다.

* Styling

  * 테그의 **<>**안에 `style="property:value"` 형식으로 작성

  * `<p style="color : cyan">`p테그 안의 글씨 색을 cyan 으로 설정`</p>`

  * <p style="color : cyan">p테그 안의 글씨 색을 cyan 으로 설정</p>

  * Style을 적용하는 세가지 방법

    * Inline - using a style attribute in HTML elements

      ```html
      <h1 style="color:blue">This is a Blue Heading</h1>
      ```

    * Internal - using a **<style>** element in the HTML **<head>** section

      ```html
      <head>
          <Style>
              h1 {
                  color:blue;
              }
          </Style>
      </head>
      ```

    * External - using one or more extenal CSS files

      ```html
      <head>
          <link rel="stylesheet" href="styles.css">
      </head>
      ```

      

<h2 style = color:peru>CSS</h2>

---

* Font

  * font-size는 **px(19px), pt(12pt), cm(13cm), %(100%)**등의 단위로 지정하거나 xx-small, x-small, **medium(기본값)**, large, x-large, xx-large 로 사용할 수 있음. *( **()** 안의 값은 기본값.)*

* 테그에 id 혹은 class 명을 지정하여 그 id 혹은 class에만 CSS를 적용할 수 있다.*(.class명, #id명)*

  ```html
  <style>
  	p#p01 {	color: blue;	}
      p.error {	color:red;	}
  </style>
  <body>
      <p id="p01">I am different.</p>
      <p class="error">I am different too.</p>
  </body>
  ```



## emmet

---

* html, css등을 작성할 때, 시간을 단축시켜주는 확장기능!
* emmet플러그인만 설치되어 있다면 사용가능!!

####  기본문법

* **`div>ul>li`** : **자식 요소**

  ```html
  <div>
      <ul>
          <li></li>
      </ul>
  </div>
  ```

* **`div+p+bq`** : **형제 요소**, 같은 단계에 위치한 요소를 생성

  ```html
  <div></div>
  <p></p>
  <blockquote></blockquote>
  ```

* **`ul>li*5`** : *n : n개 생성

  ```html
  <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
  </ul>
  ```

* **`ul>li.item$*5`** or **`ul>li#item$*5`** : **.** 은 class, **#** 은 id

  ```html
  <ul>
      <li class="item1"></li>
      <li class="item2"></li>
      <li class="item3"></li>
      <li class="item4"></li>
      <li class="item5"></li>
  </ul>
  ```

* `div+div>p>span+em^bq` : **^** 한 단계 위에 요소를 배치

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

* `div+div>span>p>span+em^^bq` : ^^ 두 단계 위에 요소를 배치, **^^...^** ^^...^단계 위에! 

  ```html
  <div></div>
  <div>
      <span>
          <p><span></span><em></em></p>
      </span>
      <blockquote></blockquote>
  </div>
  ```

* `div>(header>ul>li*2>a)+footer>p` 

  ```html
  <div>
      <header>
          <ul>
              <li><a href=""></a></li>
              <li><a href=""></a></li>
          </ul>
      </header>
      <footer>
          <p></p>
      </footer>
  </div>
  ```

* `(div>dl>(dt+dd)*3)+footer>p`

  ```html
  <div>
    <dl>
      <dt></dt>
      <dd></dd>
      <dt></dt>
      <dd></dd>
      <dt></dt>
      <dd></dd>
    </dl>
  </div>
  <footer>
    <p></p>
  </footer>
  ```

  

* [emmet](https://nachwon.github.io/How_to_use_emmet/)

  > Che1's Blog
