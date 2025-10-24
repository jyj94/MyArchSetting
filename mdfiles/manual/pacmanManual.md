# 패키지 설치
```
sudo pacman -S <패키지명> <패키지명>...
```
여러 패키지 한번에 설치 가능

# 패키지 삭제
```
sudo pacman -R <패키지명>   #패키지만 삭제
sudo pacman -Rs <패키지명>  #다른 프로그램에 연관되지 않은 의존성 함께 삭제
sudo pacman -Rsn <패키지명> #설정파일도 삭제
```

# 패키지 검색
```
sudo pacman -Ss <검색어>    #리포지토리에서 검색
sudo pacman -Qs <검색어>    #설치된 패키지에서 검색
```
# 시스템 업데이트
```
sudo pacman -Syu
```
리포지토리 동기화 + 설치된 패키지 업데이트
# 패키지 정보 확인
```
pacman -Qi <패키지명>       # 설치된 패키지 정보
pacman -Si <패키지명>       # 리포지토리 패키지 정보
```
* ```-qi``` : 설치된 패키지에 대한 정보
* ```-Si``` : 리포지토리에서의 정보 / 최신 버전, 설명, 의존성, 다운로드 크기 등

# 캐시 관리
```
sudo pacman -Sc       # 오래된 패키지 캐시 삭제
sudo pacman -Scc      # 캐시 전체 삭제
```

# 기타 옵션
```
sudo pacman -Qdt    # 불필요한 의존성 확인
sudo pacman -Qm     # AUR 등 외부에서 설치된 패키지 확인

# 패키지 목록
```
pacman -Q       # 설치한 패키지 리스트 보기
pacman -Qs      # 의존성 목록 제외
pacman -Qe      # 직접 설치한 것만 보기
```