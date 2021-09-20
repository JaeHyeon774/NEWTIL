<h1>Java Script</h1>

---

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



