---
##### - 도커 서비스 중지
```
$ systemctl stop docker
```
##### - root-dir 생성
```
$ mkdir -p docker-volume
```
##### - 장치 초기화
```
$ fdisk /dev/{device-name}
$ n (new)
$ p (partition)
$ enter / enter
$ w (write)

- 만약 xfs타입이아니라면 다른방법으로 파일시스템 만들 것 (ex. ext4)
$ mkfs.xfs -f /dev/{device-name}
```
##### - 마운트
```
$ mount -o pquota /dev/{device-name} {dir-name}
$ vi /etc/fstab
/dev/{device-name}  {dir-name}  xfs   defaults,pquota 0 0
```
##### - docker daemon.json 수정
```
- 필요 시 각 워커노드,GPU노드에서 수행
$ vi /etc/docker/daemon.json
    "data-root": "디렉토리명",   << 추가
```
##### - grub 수정 및 리부트
```
$ vi /etc/default/grub
GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet rootflags=pquota"
(마지막에 rootflags=pquota 추가)

$ systemctl daemon-reload
$ grub2-mkconfig -o /boot/grub2/grub.cfg
$ reboot
```
