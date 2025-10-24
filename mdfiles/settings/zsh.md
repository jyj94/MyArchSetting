# zsh 설치
```sudo pacman -S zsh```

# 기본 쉘로 설정
```chsh -s $(which zsh)```

# 무슨 쉘인지 확인하기
```echo $SHELL```

# oh-my-zsh 설치
## 설치
```sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
## ~/.zshrc 편집
```
ZSH_THEME="agnoster"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## 플러그인 설치
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

## 적용
```
source ~/.zshrc
```

## 외부테마 powerlevel10k 설정
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
```
~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"
```