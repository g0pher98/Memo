# 자바스크립트를 이용하여 테이블 복사하기
개발도중에 html 테이블을 복사해야하는 업무가 생겼다. 엑셀이나 한글에 붙여넣기 하려면 style까지 유지한 보이는 테이블 그대로가 필요했다.

해답은 이곳에서 찾을 수 있다.(https://stackoverflow.com/questions/2044616/select-a-complete-table-with-javascript-to-be-copied-to-clipboard)

### html
```html
<table id="tableId" border="1">
	<thead>
		<tr><th>Heading 1</th><th>Heading 2</th></tr>
	</thead>
	<tbody>
		<tr><td>cell 1</td><td>cell 2</td></tr>
	</tbody>
</table>

<input type="button" value="select table" onclick="selectElementContents( document.getElementById('tableId') );">
```

### javascript
```javascript
function selectElementContents(el) {
	var body = document.body, range, sel;
	if (document.createRange && window.getSelection) {
		range = document.createRange();
		sel = window.getSelection();
		sel.removeAllRanges();
		try {
			range.selectNodeContents(el);
			sel.addRange(range);
		} catch (e) {
			range.selectNode(el);
			sel.addRange(range);
		}
	} else if (body.createTextRange) {
		range = body.createTextRange();
		range.moveToElementText(el);
		range.select();
	}
}
```

붙여넣기하려는 소프트웨어에 따라 다르겠지만 한글의 경우 style 적용이 생각보다 까다롭다. 타 css의 영향을 받지 않도록 주의하자.