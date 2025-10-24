# 스냅샷 만들기
```
sudo timeshift --create --comments "스냅샷 이름"
```

# 스냅샷 목록 보기
```
sudo timeshift --list
```

# 복원하기
```
sudo timeshift --restore --snapshot "스냅샷명"
```

# 자동 스냅샷 활성화
```
sudo systemctl enable --now cronie.service
```
