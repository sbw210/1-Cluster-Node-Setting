

---
###### (1) Calico Node Peer IP 설정(인식)

###### IP AUTODETECTION METHOD key:value 추가
```
# Auto-detect the BGP IP address.
- name: IP
  value: "autodetect"
- name: IP_AUTODETECTION_METHOD
  value: "cider=103.212.223.192/28"
```

---


###### (2) Calicoctl 설치 [버전 항상 최신화할 것]
```
cd /usr/local/bin
curl -L https://github.com/projectcalico/calico/releases/download/v3.23.2/calicoctl-linux-amd64 -o calicoctl
chmod +x calicoctl
```

