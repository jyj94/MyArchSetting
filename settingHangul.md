# 폰트 설정
<code>/usr/share/fonts</code> 디렉터리에 폰트 저장

나의 경우 Noto Sanf CJK 폰트를 선택했다.

<pre><code>mv NotoSansCJK-VF.otf.ttc NotoSansMonoCJK-VF.otf.ttc /usr/share/fonts/NoTOSansCJK/ #하위 디렉터리에 저장</code></pre>

# 한글 입력기 fcitx5 설정
<pre><code>sudo pacman -S fcitx5-im fcitx5-hangul fcitx5-configtool #fcitx5 설치</code></pre>

<code>/etc/profile</code> 파일의 마지막 부분에 아래 구문 추가
<pre><code># hangul fcitx5 setting
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
export SDL_IM_MODULE=fcitx
export GLFW_IM_MODULE=fcitx
</code></pre>
자동으로 실행되도록 Hyprland 설정파일(<code>~/.config/hypr/hyprland.conf</code>)에 명령어 추가

<pre><code>#################
### AUTOSTART ###
#################

# Autostart necessary processes (like notifications daemons, status bars, etc.)
# Or execute your favorite apps at launch like this:

# exec-once = $terminal
# exec-once = nm-applet &
# exec-once = waybar & hyprpaper & firefox

<b>exec = fcitx5</b>
</code></pre>
fcitx5와 fcitx5-configtool를 실행하고 한글을 설정한다.
<pre><code>fcitx5 &
fcitx5-configtool</code></pre>
Available Input Method에서 hangul을 찾아 추가하고 
Global Option에서 trigger Input Method에 원하는 키 추가

나의 경우 Right Alt키를 적용했는데 다른 시스템 단축키도 입력이 되서 Right Alt를 사용하지 않는 펑션키로 매핑하였다.
<pre><code>sudo pacman -S keyd
nvim /etc/keyd/default.conf</code></pre>
<pre><code>[ids]
*

[main]
rightalt = f16</code></pre>
Input Method를 클릭하고 rightalt를 누르면 f16이 적용된다.
