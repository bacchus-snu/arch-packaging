# `bacchus-nss-sync`
[id]의 사용자 정보를 `/etc/passwd.cache`와 `/etc/group.cache`로 동기화해 `libnss-cache`가 사용할 수
있게 하는 [systemd 유닛][systemd.unit]입니다.

## 설치 (Arch Linux)
```
makepkg -si
```

## 지금 바로 동기화하기
```
sudo systemctl start bacchus-nss-sync.service
```

`bacchus-nss-sync.service`는 oneshot 서비스를 정의한 [서비스 유닛][systemd.service]입니다.  **이
서비스를 `enable`하는 것은 큰 의미가 없으니 주의하세요.** 주기적인 실행을 위해서는 아래에 적힌
것처럼 타이머를 enable해야 합니다.

## 주기적으로 동기화하게 하기
```
sudo systemctl enable --now bacchus-nss-sync.timer
```
`bacchus-nss-sync.timer`는 `bacchus-nss-sync.service`를 매일 자정에 실행하는
[타이머 유닛][systemd.timer]입니다. 뒤의 `.timer`까지 적어야 합니다.

[id]: https://id.snucse.org/
[systemd.unit]: https://man.archlinux.org/man/systemd.unit.5
[systemd.service]: https://man.archlinux.org/man/systemd.service.5
[systemd.timer]: https://man.archlinux.org/man/systemd.timer.5
