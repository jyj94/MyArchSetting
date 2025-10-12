# ALSA 설치
<pre><code>sudo pacman -S alsa-utils
aplay -l
alsamixer</code></pre>

# GUI 조작 프로그램 설치
<pre><code>sudo pacman -S pavucontrol
pavucontrol</code></pre>

# pipewire 설치
<pre><code>sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber</code></pre>

* pipewire: 본체
* pipewire-alsa: ALSA 장치를 PipeWire가 대신 관리하게 함
* pipewire-pulse: PulseAudio API 호환 (옛날 프로그램들이 이걸 씀)
* pipewire-jack: JACK 호환 (음악 작업용 프로그램용)
* wireplumber: 세션 매니저, 장치 인식·정책 담당

# 서비스 활성화
pipewire는 사용자 단위 데몬으로 --user를 붙여야함
<pre><code>systemctl --user enable --now pipewire pipewire-pulse wireplumber
</code></pre>

# 오디오 설정
재부팅을 하고 <code>pavucontrol</code>을 입력해서 GUI에서 본인의 장치를 선택
