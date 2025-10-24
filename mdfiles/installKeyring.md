# kwallet 설치
```sudo pacman -S kwallet kwalletmanager



Gnome keyring으로 선택(더 범용성이 좋음)
<pre><code>sudo pacman -S gnome-keyring libsecret seahorse</code></pre>
* gnome-keyring : 핵심 데몬
* libsecret : 다른 앱들이 keyring에 접근할 때 필요한 라이브러리
* seahorse : GUI 관리도구 (선택 사항, 없어도 됨)

# PAM(로그인 시 자동 잠금해제) 설정
<code>/etc/pam.d/login</code> 파일을 열고, 맨 아래에 아래 두 줄을 추가
<pre><code>auth       optional     pam_gnome_keyring.so
session    optional     pam_gnome_keyring.so auto_start</pre></code>