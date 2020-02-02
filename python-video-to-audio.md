# Python video to audio
영어공부를 하다가 비디오를 오디오로 변환해야했다. 로우한 방법이 있겠지만 편하게 모듈을 사용하기로 했다. `moviepy`라는 모듈을 이용하면 아래와 같이 쉽게 변환할 수 있다.
### install
``` bash
python -m pip install moviepy
```
### python code
``` python
from moviepy.editor import *
v = VideoFileClip('video.mp4')
v.audio.write_audiofile('audio.mp3')
```

## 참고
https://stackoverflow.com/questions/55081352/how-to-convert-mp4-to-mp3-using-python