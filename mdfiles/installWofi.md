# wofi(앱 실행기) 설치
<pre><code>sudo pacman -S wofi</code></pre>

# 설정 파일
1. 설정 파일 ```~/.config/wofi/config```
2. css 설정 파일 ```~/.config/wofi/style.css```

config 파일
```
mode=drun
width=20% #넓이
location=center # 시작 위치
allow_images=true # 프로그램 아이콘 표시
insensitive=true
prompt=Run:
hide_scroll=true # wofi에서 스크롤 안보이게
no_actions=true # 프로그램 액션 표시 제거
normal_window=true # layershell 대신 일반 윈도우로 표시
```

style.css 파일
```
/* 전체 윈도우 */
#window {
    margin: 15px;
    background-color: rgba(18,18,18,0.5); /* 어두운 배경 */
    border-radius: 10px;
}

/* 입력창 */
#input {
    margin: 12px;
    border: none; /* 전체 테두리 제거 */
    border-bottom: 2px solid #FF8800; /* 아래쪽만 테두리 */
    background-color: rgba(18,18,18,0);
    border-radius: 0px; /* 아래 테두리만 살릴 거면 모서리 둥글기 제거 */
    color: #FF8800;
    font-size: 20px;
    padding: 4px; /* 입력창 안쪽 여백 */
}
#input:focus {
    outline: none;
    box-shadow: none;
    border: none;    
    border-bottom: 2px solid #FF8800; /* 아래쪽만 테두리 */

}
/* 내부 박스 */
#inner-box {
    margin: 5px;
}

/* 외부 박스 */
#outer-box {
    margin: 5px;
}


/* 텍스트 박스 */
#text {
    margin: 5px;
    color: #EAEAEA;
    border-radius: 20px;
}

/* 선택된 엔트리 */
#entry:selected {
    margin: 5px;
    border: 2px solid #FF8800;
    background-color: #FF8800;
    color: #121212; /* 선택 시 텍스트 대비 */
    border-radius: 10px;
}
```

# 하나만 뜨게 설정
```
~/.config/hypr/hyprland.conf
...
windowrule = stayfocused, class: wofi
windowrule = noborder, class: wofi
...
```