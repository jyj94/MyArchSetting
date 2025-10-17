# Dolphin 설치
```
sudo pacman -S dolphin
qt6-multimedia-ffmpeg 1번 선택

sudo pacman -S qt5ct qt6ct kvantum

sudo pacman -S kde-cli-tools
```

* qt5ct : QT5 기반 애플리케이션의 모양과 느낌을 설정하는 도구
* qt6ct : QT6 기반 애플리케이션의 모양과 느낌을 설정하는 도구
* kvantum : QT5, QT6 애플리케이션을 위한 커스텀 테마 엔진
# Hyprland에 설정 추가
```~/.config/hypr/hyprland.conf``` 파일에 다음 환경 변수를 추가하여 QT 애플리케이션이 ```qt6ct```을 사용하도록 지정

# Kvantum 테마 적용
터미널에서 kvantummanager를 실행하여 원하는 테마(예: Catppuccin, Nord 등의 Kvantum 버전)를 선택하고 Dolphin의 디자인을 Hyprland와 완벽하게 일치시키면 됩니다.