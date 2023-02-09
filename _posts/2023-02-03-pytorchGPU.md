---
layout: post
title: Python) PyTorch GPU Installation
categories: Python
tags: [Python, PyTorch, CUDA, AI]
---
&nbsp;&nbsp;<i>PyTorch</i> is a powerful deep learning module. There are two version of PyTorch, <i>PyTorch CPU</i> and <i>PyTorch GPU</i>. If you want to run own program more fast, you need to use <i>PyTorch GPU</i>. In this post, I introduce how to install the module in <i>Anaconda</i> env.

## 1. Check the versions of dependencies
<hr>
&nbsp;&nbsp;To use PyTorch GPU, you must already install <i>NVIDIA CUDA</i>.

1. Check CUDA Compute Capability of your GPU. You can check CUDA Compute Capability of your GPU from <a href = "https://developer.nvidia.com/cuda-gpus#compute">NVDIA developer</a>. Almost GPU whose CUDA Compute Capability is more than 3.5 can run CUDA.

2. Find <i>CUDA Toolkit<i> version campatible with you GPU from <a href = "https://en.wikipedia.org/wiki/CUDA">CUDA wikipedia</a>.

3. <a href = "https://www.nvidia.com/Download/index.aspx?lang=kr">Update your GPU driver</a>.

4. Check CUDA Toolkit version supported PyTorch from <a href = "https://pytorch.org/">PyTorch website</a>.
    
    <img src = "https://user-images.githubusercontent.com/80208196/216701185-0315c517-2f92-4d27-98a9-eb39962f7fdb.png">

    > My GPU is GeForce GTX 1660 Ti whose CUDA Compute Capability is 7.5. And the stable version PyTorch supports CUDA 11.6. So I installed CUDA Toolkit 11.6.

<br/><br/>

## 2. Install CUDA, cuDNN and PyTorch
<hr>

1. Install CUDA Toolkit from <a href="https://developer.nvidia.com/cuda-toolkit-archive">NVIDIA CUDA Toolkit Archive</a>.

2. Install <i>NVDIA CUDA Deep Neural Network Library(cuDNN)</i>. Before installation, you have to check the version of cuDNN that is compatible with CUDA Toolkit version which you choose. You can do both from <a href = "https://developer.nvidia.com/rdp/cudnn-archive">cuDNN Archive</a>. (You have to sign-in NVDIA DEVELOPER)

3. Check whether there are `CUDA_PATH` and `CUDA_PATH_V11_6`(version is yours) in environment variable. If they are not, add the CUDA PATH.

    <script src="https://gist.github.com/unsik6/d88ffef28b2a8addb3b9f23642805230.js"></script>

    You have to change the version to yours.

4. Install PyTorch using the command that you can get from <a href = "https://pytorch.org/">PyTorch website</a>.

    <script src="https://gist.github.com/unsik6/96d113ff667e417909016a3d15fbf047.js"></script>

5. Check the PyTorch version and CUDA availability.

    <script src="https://gist.github.com/unsik6/3f74b998da4763d8bff1941683e7e4ee.js"></script>

    <img src = "https://user-images.githubusercontent.com/80208196/216703492-8bf0ce1b-1af7-4f5b-ae40-7ae5426ddbeb.png">

<br/><br/>

## 3. cuda.available: False
<hr>
&nbsp;&nbsp;If `torch.cuda.is_available()` returns `False` although you installed PyTorch GPU, The version of dependencies is not correct or compatible. Check whether your GPU supports CUDA from NVDIA Forum. Change versions of your CUDA, cuDNN and PyTorch.

<br/><br/>

## Refers
<hr>
<a href = "https://developer.nvidia.com/"><i>NVDIA DEVELOPER</i> </a><br/>
<a href = "https://en.wikipedia.org/wiki/CUDA">CUDA wikipedia</a><br/>
<a href = "https://pytorch.org/">PyTorch</a><br/>
<a href = "https://076923.github.io/posts/Python-pytorch-1/">Daehee YUN Tech Blog, "Python Pytorch 강좌 : 제 1강 - PyTorch 소개 및 설치"</a><br/>
<a href = "https://afsdzvcx123.tistory.com/entry/%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5-Windows%EC%9C%88%EB%8F%84%EC%9A%B0-CUDA-cuDNN-%EC%84%A4%EC%B9%98%EB%B0%A9%EB%B2%95">BeomBeomJoJo, "[인공지능] Windows(윈도우) CUDA, cuDNN 설치방법"</a><br/>
<a href = "https://hanryang1125.tistory.com/13">코딩연습장, "NVDIA CUDA 및 cuDNN 설치 (Windows)"</a><br/>