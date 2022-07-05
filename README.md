# Cluster-Node-Setting

#### Cluster Node 설정
---
- 노드 Disk 최소 2개 이상 필요 (OS용/Docker-Volume용)
- Worker와 GPU의 docker daemon.json 파일 형태 다름
- data-transfer용 노드 라벨링 (taint 설정 추가필요)
- gpu용 노드 라벨링
---
#### Hide Process 
---
- 출저: https://github.com/gianlucaborello/libprocesshider
- 모든 worker & GPU 노드에 배포 및 설치 필요
- 사전 설치필요 패키지 : gcc
---
#### Ceph-CSI
---
