# Reverse

## Fragile

简单异或

> rtcp{h3y_1ts_n0t_b4d}

## Breakable

```java
String flag = "";
String s1 = "k33p_1t_in_pl41n";
String s2 = "ÒdÝ¾¤¤¾ÙàåÐcÝÆ¥ÌÈáÏÜ¦aã";
int len = s2.length() / 2;
int i = 0;

for(i = 0; i < 2; i++){
    flag += (char)((int)(s2.charAt(i + len)) - (int)(s1.charAt(i + 2)));
}

for(i = 0; i < len; i++){
    flag += (char)((int)(s2.charAt(i)) - (int)(s1.charAt(i)));
}
System.out.println(flag);
```

> rtcp{0mg_1m_s0_pr0ud_}

## EZ

打开py文件就是

> rtcp{tH1s_i5_4_r3aL_fL4g_s0_Do_sUbm1T_1t!}

## PZ

> rtcp{iT5_s1mPlY_1n_tH3_C0d3}

## LEMON

> rtcp{y34H_tHiS_a1nT_sEcuR3}

## SQUEEZY

> rtcp{y0u_L3fT_y0uR_x0r_K3y_bEh1nD!}

## thedanzman

```python
import base64
import codecs

s1 = "'=ZkXipjPiLIXRpIYTpQHpjSQkxIIFbQCK1FR3DuJZxtPAtkR'o"
s1 = s1[::-1]
print(s1)
s1 = codecs.decode(s1, "rot_13")[2:-1].encode()
print(s1, type(s1))
s1 = base64.b64decode(s1)
print(s1)
s2 = "nyameowpurrpurrnyanyapurrpurrnyanya"
s2 = codecs.encode(s2, "rot_13")
s2 = s2.encode()

ss = [chr(v1 ^ v2) for v1, v2 in zip(s1, s2)]
ss = "".join(ss)
print(ss)
```

> rtcp{n0w_tH4T_w45_m0r3_cH4lL3NgiNG}