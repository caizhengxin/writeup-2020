# VirSecCon

## Steganography

### Elessbe

zsteg

> LLS{lsb_est_mon_bon_ami}

## Forensics

### Tragic Number

修改文件头504b0304

> LLS{tragic_number_more_like_magic_number}

## Miscellaneous

### Hidden

cat .secret/._dont_delete_me.txt

> LLS{you_found_my_hidden_secrets}

## Cryptography

### Polybius

https://www.dcode.fr/polybius-cipher

> POLYBIUSSQUAREISNOTTHATHARD

### Classic

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

# 分解n，http://www.factordb.com/index.php
p = 269967471399519356371128763174813106357
q = 287545525236502653835798598413374134819
e = 65537
c = 62899945974090753231979111677615029855602721049941681356856158761811378918268


d = gmpy2.invert(e, (p - 1) * (q - 1))
m = gmpy2.powmod(c, d, p * q)
m = long_to_bytes(m)
print(m)
```

> LLS{just_another_rsa_chal}

### Old Monitor

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


n1 = 7156756869076785933541721538001332468058823716463367176522928415602207483494410804148006276542112924303341451770810669016327730854877940615498537882480613
n2 = 11836621785229749981615163446485056779734671669107550651518896061047640407932488359788368655821120768954153926193557467079978964149306743349885823110789383
n3 = 7860042756393802290666610238184735974292004010562137537294207072770895340863879606654646472733984175066809691749398560891393841950513254137326295011918329
c1 = 816151508695124692025633485671582530587173533405103918082547285368266333808269829205740958345854863854731967136976590635352281190694769505260562565301138
c2 = 8998140232866629819387815907247927277743959734393727442896220493056828525538465067439667506161727590154084150282859497318610746474659806170461730118307571
c3 = 3488305941609131204120284497226034329328885177230154449259214328225710811259179072441462596230940261693534332200171468394304414412261146069175272094960414
e = 0x3
n =  [n1, n2, n3]
c =  [c1, c2, c3]


def CRT(mi, ai):
    assert(reduce(gmpy2.gcd,mi)==1)
    assert (isinstance(mi, list) and isinstance(ai, list))
    M = reduce(lambda x, y: x * y, mi)
    ai_ti_Mi = [a * (M / m) * gmpy2.invert(M / m, m) for (m, a) in zip(mi, ai)]
    return reduce(lambda x, y: x + y, ai_ti_Mi) % M


m=gmpy2.iroot(CRT(n, c), e)[0]
print(long_to_bytes(m))
# LLS{the_chinese_remainder_theorem_is_so_cool}
```

## Social Media Sham

### Github

头像下面

> LLS{this_might_help_other_challenges}

### Instagram

> LLS{i_hate_this_social_media_platform}

### YouTuBe

> LLS{like_comment_and_subscribe}

### Discord

> LLS{discord_is_better_than_slack}

### LinkedIn

> LLS{pRoFeSsIoNaL_nEtWorK_LOL}

### Twitter

> LLS{thank_you_for_your_support}

## Warmup

### Belive Your Eyes

winhex打开压缩包，搜索LLS

> LLS{if_ten_million_fireflies}

### Yarn

winhex打开压缩包，搜索LLS

> LLS{it_was_just_a_ball_of_strings}

### Ssh, quiet!

ssh user@jh2i.com -p 50035 cat flag.txt

> LLS{automate_ssh_like_a_boss}

### Pack'd

winhex

> LLS{?an_ex瞵菘8utable_cbdw_da浀磔*}