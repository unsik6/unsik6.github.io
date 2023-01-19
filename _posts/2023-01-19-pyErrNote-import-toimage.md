---
layout: post
title: Python) Error - scipy.misc.toimage
subtitle: How to convert float32 matrix to image
categories: Python
tags: [Python, Error Note, AI, ML, DL]
---
## 1. Error
<hr>

> <span style="color:red">ImportError: cannot import name 'toimage' from 'scipy.misc'</span>

&nbsp;&nbsp;I was learning image processing in DL lecture. I had to convert float32 matrices into images. In the lecture, the code below is proposed.

```python
from scipy.misc import toimage
fig = plt.figure(figsize = (20, 2))
for i in range(0, n):
    ax = fig.sadd_subplot(1, n, i+1)
    ax.imshow(toimage(matrices[i]))
```
&nbsp;&nbsp;`matrices[i].shape` is `32, 32, 3`, and 'matrices' save float32 value. The last dimension whose shape is 3 means the channel of images is RGB. But the code above did not work.

<br/><br/>

## 2. Reason
<hr>
&nbsp;&nbsp;`scipy.misc.toimag` is removed since version 1.2. The <a href = "https://docs.scipy.org/doc/scipy-1.1.0/reference/generated/scipy.misc.toimage.html#scipy.misc.toimage">documentation</a> suggests using `PIL.Image.fromarray`.

> `toimage` is deprecated! `toimage` is deprecated in SciPy 1.0.0, and will be removed in 1.2.0. Use Pillow’s `Image.fromarray` directly instead.

<br/><br/>

## 3. Solutions
<hr>

### 1) Downgrade scipy module
<hr>
&nbsp;&nbsp;The first solution is downgrading `scipy` module. Uninstall first, if you already installed that.

```bash
pip uninstall scipy
pip install scipy = 1.1.0
```

<br/>

### 2) Use PIL.Image
<hr>
&nbsp;&nbsp;This solution is following the suggetion of the documentation of <i>Scipy</i>.

1. First, install `pillow` module, or install `image` module directly.
    ```bash
    pip install pillow
    ```
    or,
    ```bash
    conda install pillow
    ```
<br/>

2. Convert float32 values to 0-255 int8 format. Then, you can use `Image.fromarray` with the default mode.
    ```python
    formatted = (matrices[i] * 255 / np.max(matrices[i])).astype('uint8')
    img = Image.fromarray(formatted)    # convert to image
    ```

    &nbsp;&nbsp;There are many modes of `Image.fromarray`. Check <a href = "https://pillow.readthedocs.io/en/stable/handbook/concepts.html#concept-modes">the documentation of pillow</a>, and convert your array to an appropriate type.

<br/>

### 3) Just convert type to 0-255 int type
<hr>
&nbsp;&nbsp;Because I used `matplotlib.imshow`, I could show the image using int matrix without converting that to an image.

```python
    formatted = (matrices[i] * 255 / np.max(matrices[i])).astype('uint8')
    plt.imshow(formatted)
```
<br/><br/>

## Refers
<hr>
<a href = "https://docs.scipy.org/doc/scipy-1.1.0/reference/generated/scipy.misc.toimage.html#scipy.misc.toimage"><i>SciPy.org</i> (documentation)</a><br/>
<a href = "https://pillow.readthedocs.io/en/stable/index.html">Docs of <i>Pillow</i> </a><br/>
<a href = "https://stackoverflow.com/questions/38867869/how-to-create-image-from-numpy-float32-array">stack overflow, "How to create image from numpy float32 array?"</a><br/>
<a href = "https://stackoverflow.com/questions/62708777/importerror-with-scipy-misc-cannot-import-toimage">stack overflow, "ImportError with scipy.misc cannot import toimage"</a><br/>
<a href = "https://robot9710.tistory.com/5">ROBOT공학자, "[Python] scipy에서 imread가 안읽혀!!! ( ImportError: cannot import name 'imread' )"</a>