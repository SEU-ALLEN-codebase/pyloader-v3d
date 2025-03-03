# Vaa3D in Python Made Easy
Python library for Vaa3D functions.

## Installation

```shell
$ pip install v3d-py-helper
```

By cloning the repo and test the Cyhton usages:
```shell
$ python setup.py build_ext --inplace
```

## Usage

### Loading Vaa3D format data

```python
from v3dpy.loaders import Raw, PBD

raw = Raw()
img = raw.load('path.v3draw')
raw.save('path.v3draw', img)

pbd = PBD()
img = pbd.load('path.v3dpbd')
pbd.save('path.v3dpbd', img)
```

### Loading TeraFly format data

Currently only support Tiff 3D tiles.

```python
from v3dpy.terafly import TeraflyInterface
import numpy as np

t = TeraflyInterface('teraconvert_path')
x, y, z, c = t.get_dim()
# center block
size = np.array(t.get_dim()[:3])
half_block_size = np.array([128, 128, 64]) // 2
start = size // 2 - half_block_size
end = size // 2 + half_block_size - 1

# 4D image, indexed by c, z, y, x 
img = t.get_sub_volume(start[0], end[0], start[1], end[1], start[2], end[2])
```

## Toubleshooting

On Windows, MS BuildTool >= 16 is required to build the wheel.

Newer setuptools seem to be buggy.

Once successfully installed, the package can still report import error, which suggests some of the runtime libs, especially those related with compression, are missing in you machine.


## Useful Links

Github project: https://github.com/SEU-ALLEN-codebase/v3d-py-helper

Vaa3D source: https://github.com/Vaa3D/v3d_external

Documentation: https://SEU-ALLEN-codebase.github.io/v3d-py-helper

# Contact
Main Developer: Zuohan Zhao  
My GitHub Page: https://github.com/zzhmark  
Email: zzhmark@126.com
