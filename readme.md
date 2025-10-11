# Arch Linux 설치
## 파티션 설정
### 디스크 구조 확인 
<pre><code>lsblk</code></pre>

### 파티션 도구 fdisk
<pre><code>fdisk</code></pre>

디스크 선택
<pre><code>fdisk /dev/sda</code></pre>

MBR에서 GPT로 변경
<pre><code>g</code></pre>

EFI 파티션 생성
<pre><code>n 새로운 파티션 생성
1 첫번째 파티션
2048 첫 섹터
+512M 512MB 공간 설정
t 파티션 종류 설정
1 EFI System</code></pre>

리눅스 파티션 생성
<pre><code>n 새로운 파티션 생성
2 두번째 파티션 생성
Enter : 첫 섹터 시작은 마지막 지점
Enter : 마지막 섹터는 끝까지</code></pre>

작성한 내용 저장
<pre><code>w</code></pre>

### 포맷
/dev/sda1은 fat32로
/dev/sda2는 ext4로 포맷한다.
<pre><code>mkfs.fat -F32 /dev/sda1
mkfs.ext /dev/sda2</code></pre>

### 파티션 마운트
<pre><code>mount /dev/sda2 /mnt
mkdir -p /mnt/boot/efi
mount /dev/sda1 /mnt/boot/efi</code></pre>

## Arch 설치
<pre><code>pacstrap /mnt base linux linux-firmware neovim sudo networkmanager</code></pre>

## fstab 생성
<pre><code>genfstab -U /mnt >> /mnt/etc/fstab</code></pre>

## chroot로 시스템 진입
<pre><code>arch-chroot /mnt</code></pre>

## 리눅스 설정
### root 비밀번호 설정
<pre><code>passwd root</code></pre>

### 사용자 추가
<pre><code>useradd -m username
passwd username</code></pre>

### 사용자 wheel 그룹에 추가(sudo를 위해)
<pre><code>usermod -aG wheel username
EDITOR=nvim visudo
visudo</code></pre>
이후 <code>#%wheel ALL=(ALL) ALL</code>구문에서 #을 지워 문장 활성화

### 시간대 설정
<pre><code>ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
hwclock --systohc</code></pre>

### 로케일 설정
<pre><code>echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
echo "ko_KR.UTF-8 UTF-8" >> /etc/locale.gen
locale-gen
</code></pre>

### 호스트네임 설정
<pre><code>echo "JYJArch" > /etc/hostname</code></pre>

### 네트워크 관리자 systemctl에 추가
<pre><code>systemctl enable NetworkManager</code></pre>

### 부트로더(Grub) 설치
<pre><code>pacman -S efibootmgr grub
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg</code></pre>

### initramfs 설치 
<pre><code>mkinitcpio -P</code></pre>

### 종료하기
<pre><code>exit
reboot</code></pre>
종료 후 바이오스에서 설치 디스크나 GRUB으로 표시된 부트 항목을 선택한다.
위에서 생성한 사용자 계정으로 로그인한다.

### GRUB 수정하기
리스트에서 선택하는 것 대신 바로 Archi linux로 부팅하게 수정
1. /etc/default/grub 파일 수정
<pre><code>nvim /etc/default/grub

GRUB_TIMEOUT=0       # 메뉴 표시 시간 0초
GRUB_TIMEOUT_STYLE=hidden  # 메뉴 숨김
GRUB_DEFAULT=0       # 기본 부팅 항목 (0번째 = 첫 번째)

:wq
</code></pre>
2. 수정한 내용으로 cfg 파일 생성
<pre><code>sudo grub-mkconfig /boot/grub/grub.cfg</code></pre>
3. 재부팅하여 적용이 됐는지 확인한다.
<pre><code>reboot</code></pre>

# Hyprland 설치
<pre><code>sudo pacman -S hyprland kitty</code></pre>


### 
<pre><code></code></pre>