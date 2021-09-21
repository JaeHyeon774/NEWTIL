<h1>Java Script</h1>

---

* HTML과 Server Script(Back-end) 사이에서 접속자의 마우스 클릭, 키보드 입력등 이벤트 처리를 주로 담당.

  출력(HTML+CSS) <---> 동작/이벤트(Javascript) <---> 데이터베이스 접속 처리(백앤드)









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



