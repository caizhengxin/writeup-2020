# Misc

## About

签到

> hexCTF{mu5t_b3_7he_eas1est_fl4g_y0u_g0t}

## Mirage

1. F12进入调试模式，发现hexfont.ttf

```python
import string


table = string.ascii_letters + "1234567890" + "{}_"
key = "dBFS4f}jZE5gRsAKOp1m20xt8hwcevoyGz1TJ{VDMQ39iquC7WXNHLYUaPkr6_" + "bnI"
c = "j4teqybvAskIE2S}4IdIc_M5IB8IHm1IF_0Ypn"

for s in c:
    m = table[key.find(s)]
    print(m, end="")

print("\n")
# hexCTF{Don7_judge_a_B0Ok_by_1ts_c0v3r}
```

> hexCTF{Don7_judge_a_B0Ok_by_1ts_c0v3r}

## Hmmm

1. 盲文解密或者逆向

> hexCTF{1m_s0rry_1f_y0u_r3v3r5ed_7h1s}

## T&J

https://rgbpwn.xyz/2020/04/13/tj/

```python
import os
import matplotlib.pyplot as plt
 
 
pcapFilePath = "jerry.pcapng"
DataFileName = "usb.dat"
data = []
 
 
def main():
    X = []
    Y = []
    mouseX = 0
    mouseY = 0
 
    # get data of pcap
    command = "tshark -r %s -T fields -e usb.capdata > %s" % (pcapFilePath, DataFileName)
    print(command)
    os.system(command)
 
    # read data
    with open(DataFileName, "r") as f:
        for line in f:
            data.append(line[:8].strip())
            # depending on what tshark you have, the output may be separated by ":" instead
    # print(data)
 
    # handle each movement
    for dat in data:
        capture_data = [dat[i:i + 2] for i in range(len(dat))]
        if len(capture_data) == 8:
            horizontal = 2  # -
            vertical = 4  # |
        elif len(capture_data) == 4:
            horizontal = 1  # -
            vertical = 2  # |
        else:
            continue
 
        offsetX = int(capture_data[horizontal], 16)
        offsetY = int(capture_data[vertical], 16)
        if offsetX > 127:
            offsetX -= 256
        if offsetY > 127:
            offsetY -= 256
        mouseX += offsetX
        mouseY += offsetY
       
        # don't record the movement if the mouse is not pressed down
        if capture_data[0] == "00":
            continue
 
        X.append(mouseX)
        Y.append(-mouseY)
 
    fig = plt.figure()
    ax1 = fig.add_subplot(111)
 
    # print(X)
    # print(Y)
 
    ax1.set_title("File " + pcapFilePath)
    ax1.scatter(X[:-10], Y[:-10], s=1, c='r', marker='o')
   
    # show the plot
    plt.show()
 
    # clean temp data
    os.system("rm ./%s" % (DataFileName))
 
 
if __name__ == "__main__":
    main()
```