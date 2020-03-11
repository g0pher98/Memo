# 자바스크립트에서 label을 이용한 파일업로드
`label`태그는 보통 다른 태그를 대신하여 사용하는 태그다. 해당 라벨을 이용해 원본 태그에 포커스를 두는 방식이다.  

문제는 파일 업로드에서 일어나는데, 클릭이벤트는 잘 동작하지만 Drag&Drop 기능이 동작하지 않는다. 파일 업로드 시 label태그를 사용해야했던 이유는 file 타입의 input태그는 버튼 모양을 수정하지 못하기 때문이다. 스타일을 수정하기 위해서 label를 사용해야 했다.

해결 방안은 다음 사이트에서 찾았다.(https://stackoverflow.com/questions/49971247/drag-and-drop-a-file-on-label)

### html
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<label for="image-event" id="image-event-label">
    	Import an image
    	<input type="file" name="image-event" id="image-event">
</label>
```

### javascript
```javascript
// only to show it did change
$('#image-event').on('change', function upload(evt) {
  console.log(this.files[0]);
});

// only to show where is the drop-zone:
$('#image-event-label').on('dragenter', function() {
  this.classList.add('dragged-over');
})
 .on('dragend drop dragexit', function() {
  this.classList.remove('dragged-over');
});
```

정말 아름답게 해결된다.