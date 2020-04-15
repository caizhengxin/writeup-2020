# Crypto

## XOR

```python
import string
from random import choice
from itertools import cycle

# hexCTF{}

with open("flag.enc", "rb") as f:
    c = f.read()

flag = b"hexCTF{"

# 获取key前7个字节
key = "".join([chr(c[i] ^ flag[i]) for i in range(len(flag))])

# 爆破key后2个字节
# 输出结果找语句通顺单词
for i in string.ascii_letters:
    for j in string.ascii_letters:
        key_gen = cycle(key + i + j)

        flag = "".join([chr(c[i] ^ ord(next(key_gen))) for i in range(len(c))])

        if "}" in flag and flag[7:-1].isalpha():
            print(flag)

# hexCTF{supercalifragilisticexpialidocious}
```

> hexCTF{supercalifragilisticexpialidocious}

### SSS

- https://rgbpwn.xyz/2020/04/08/rgbpwn2/

### Really Smart Acronym

- https://rgbpwn.xyz/2020/04/12/really-smart-acronym/

```python
from pwn import *

sh = remote('challenges1.hexionteam.com', 5000)

sh.recvuntil('Flag: ')

cipher = int(sh.recvline().decode().strip())
#print(cipher)

sh.recvuntil('m => ')
sh.sendline('-1')

n = int(sh.recvline().decode().strip()) + 1

mult = pow(2, 65537, n)
#print(mult)

def get_lsb(num):
	sh.recvuntil('> ')
	sh.sendline(str(num))
	return int(sh.recvline().decode().strip())

high = n
low = 0
for i in range(1024):
	cipher *= mult
	cipher %= n
	lsb = get_lsb(cipher)
	if lsb == 0:
		high = (high + low) // 2
	else:
		low = (high + low) // 2

print(high)
```
