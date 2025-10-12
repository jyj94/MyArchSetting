# Hyprland() 설치
설치 전 pacman을 업데이트하고 hyprland kitty를 설치한다.
<pre><code>sudo pacman -Syu #S:설치/업데이트, y:패키지 데이터베이스 갱신, u:업그레이드</code></pre>
<pre><code>sudo pacman -S hyprland kitty</code></pre>

# Hyprland 실행
<pre><code>Hyprland</code></pre>

# focus policy 해제
커서를 옮기면 포커스가 옮겨나는데 이게 불편함

이게 불편해서 바꾸려함

```~/.config/hypr/hyprland.conf```에서 ```input``` 항목의
```
follow_mouse = 2
```
로 변경한다.
* 0 - Cursor movement will not change focus.
(커서 이동은 포커스를 변경하지 않습니다.)
* 1 - Cursor movement will always change focus to the window under the cursor.
(커서 이동은 항상 커서 아래에 있는 창으로 포커스를 변경합니다.)
* 2 - Cursor focus will be detached from keyboard focus. Clicking on a window will move keyboard focus to that window.
(커서 포커스는 키보드 포커스와 분리됩니다. 창을 클릭하면 해당 창으로 키보드 포커스가 이동합니다.)
* 3 - Cursor focus will be completely separate from keyboard focus. Clicking on a window will not change keyboard focus.
(커서 포커스가 키보드 포커스와 완전히 분리됩니다. 창을 클릭해도 키보드 포커스는 변경되지 않습니다.)

```hyprctl reload```로 재시작