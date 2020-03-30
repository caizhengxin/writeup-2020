# Crypto

## Alternative

> 知识点：HTTPS证书错误

> 题解

1. 打开网站，提示证书不被信任，点高级发现列出适用于域名s0.many.fields.in.certificate.com

> VolgaCTF{s0.many.fields.in.certificate.com}

## Noname

> 知识点：密钥爆破

> 题解

1. 由于密钥是和时间有关，猜测最近几天

```python
import time
import base64
from Crypto.Cipher import AES
from hashlib import md5


c = "uzF9t5fs3BC5MfPGe346gXrDmTIGGAIXJS88mZntUWoMn5fKYCxcVLmNjqwwHc2sCO3eFGGXY3cswMnO7OZXOw=="
c = base64.b64decode(c)

i = 1

while 1:
    key = md5(str(int(time.time() - i)).encode("utf-8")).digest()
    aes = AES.new(key, AES.MODE_ECB)
    m = aes.decrypt(c)

    if b"VolgaCTF" in m:
        print(m)
        break
    
    i += 1

# VolgaCTF{5om3tim3s_8rutf0rc3_i5_th3_345iest_w4y}
```

> VolgaCTF{5om3tim3s_8rutf0rc3_i5_th3_345iest_w4y}

## Keygreed

- https://sectt.github.io/writeups/Volga20/crypto_keygreed/README

## Guess

- https://github.com/saurav3199/CTF-writeups/tree/master/VolgaCTF

## Export

## Back Seat

