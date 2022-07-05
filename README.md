# [ Cluster-Node-Setting ]

### * Cluster Node 설정
---
- 노드 Disk 최소 2개 이상 필요 (OS용/Docker-Volume용)
- Worker와 GPU의 docker daemon.json 파일 형태 다름
- data-transfer용 노드 라벨링 (taint 설정 추가필요)
- gpu용 노드 라벨링
- docker volume의 root dir 설정 변경
---
### * Hide Process 
---
- 출저: https://github.com/gianlucaborello/libprocesshider
- 모든 worker & GPU 노드에 배포 및 설치 필요
- 사전 설치필요 패키지 : gcc
---
### * Ceph-CSI
---

---
### * NFS-Client
---
##### - NFS Client Package Install
```
$ yum -y install nfs-utils libnfsdimap
$ systemctl enable rpcbind
$ systemctl start rpcbind
```
##### - Check communication with NFS Server 
```
$ showmount -e {NFS Server IP}
```
##### - Mount NFS Volume
```
$ mkdir -p /{Dir Name}
$ mount {NFS Server IP}:/{Dir Name} {Dir Name}
```
##### - Check Mount Status
```
mount | grep {Dir Name}
```
##### - Mount permanently
```
$ vi /etc/fstab
{NFS Server IP}:/{Dir Name} {Dir Name}  nfs   rw,sync,hard,intr   0 0
```

