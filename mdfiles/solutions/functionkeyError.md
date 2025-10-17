# 문제
펑션키(F1~F12)가 아무런 기능을 안하고 몇개의 키가 미디어키 같은 동작만 함\
wev 프로그램으로 입력 이벤트를 살펴보면 눌러도 아무런 입력이 안뜨고 미디어키만 몇개 입력됨

# 해결법
```/sys/module/hid_apple/parameters/fnmode``` 파일 내용을 0으로 바꿈
```
sudo echo "0" > /sys/module/hid_apple/parameters/fnmode
```
