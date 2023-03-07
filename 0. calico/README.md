

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

---

###### (3) Bandwidth 제한 적용
```
config 설정에 아래 적용되어있을 시,

{
  "type": "bandwidth",
  "capabilities": { "bandwidth": true }
}

아래 yaml 구문을 활용하여 in, out bandwidth 제한 가능.
metadata:
  annotations:
    kubernetes.io/ingress-bandwidth: 1M
    kubernetes.io/egress-bandwidth: 1M
```

