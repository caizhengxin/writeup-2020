# Stego

## Curved

https://ctftime.org/writeup/19158

```python
# Reverse image search to find out it's hilbert + peano -> hilbert curves
# Generate hilbert curve of order 9, 2 (2^9 = 512, 2 = 2d)
# iterate image in hilbertCurve.transpoed order
# LSB of B bits
# PNG file
from BitVector import BitVector
from PIL import Image
from hilbertcurve.hilbertcurve import HilbertCurve
import math

img  = Image.open("stego.png")

# build a list of hilbert curve coordinates
hc = HilbertCurve(int(math.log2(img.height)), 2)
locations = [hc.coordinates_from_distance(i) for i in range(hc.max_h+1)]

# iterate the pixels in transposed hilbert curve order
bitlist = [img.getpixel((y,x))[2] & 1 for (x,y) in locations]
BitVector(bitlist=bitlist).write_to_file(open("out.png", "wb"))

Image.open("out.png")
```

## Dissolved

https://ctftime.org/writeup/19157
https://ctftime.org/writeup/19270

```python
# Blue-LSB of all pixels with alpha != 255
from BitVector import BitVector
from PIL import Image
import numpy as np

img  = Image.open("stego.png")
data = np.array(img.getdata()) # get data as np array
mask = data[:,3]!=255          # only pixels where alpha isn't max     
data = data[mask]              # apply mask
data = data[:,2]&1             # only get green LSB
BitVector(bitlist=data).get_text_from_bitvector()
```

## Toccata

## 参考

- https://ctftime.org/event/933/tasks/