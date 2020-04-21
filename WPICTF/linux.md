# linux

## LynxVE

1. 按g，输入file:///home/ctf/flag

> WPI{lynX_13_Gr8or_Th@n_Chr0m1Um}

## Suckmore Shell 2.0

```bash
ls
more flag
```

> WPI{SUckmoreSoftwareN33dz2G3TitTogeTHER}

## sigknock

1. ps -aux, 发现可疑irqknock进程
2. 尝试改变状态

```bash
~ $ kill -2 6
Got signal 2
State advanced to 1
~ $ kill -3 6
Got signal 3
State advanced to 2
~ $ kill -11 6
Got signal 11
State advanced to 3
~ $ kill -13 6
Got signal 13
State advanced to 4
~ $ kill -17 6
Got signal 17
State advanced to 5
WPI{1RQM@St3R}
```

> WPI{1RQM@St3R}