---
layout: post
title: Anaconda) Error - CondaSSLError
subtitle: Exception HTTPSConnectionPool
categories: Python
tags: [Python, Anaconda, Error Note]
---
## 1. Error
<hr>

> <span style="color:red">CondaSSLError: OpenSSL appears to be unavailable on this machine. OpenSSL is required to download and install packages.</span>
> <span style="color:red">Exception: HTTPConnectionPool(host='reop.anaconda.com', port=443): Max retries exceeded with url: /pkgs/main/win-64/setuptools-65.6.3-py310haa95532_0.conda (Caused by SSLError("Can't connect to HTTPS URL because the SSL module is not available."))</span>

&nbsp;&nbsp;When I install packages in <i>Anaconda</i> env, `CondaSSLError` appears.



<br/><br/>

## 2. Solution
<hr>

<br/><br/>

## Refers
<hr>
<a href = "https://stackoverflow.com/questions/55185945/any-conda-or-pip-operation-give-ssl-error-in-windows-10">stack overflow, "Any conda or pip operation give SSL Error in windows 10" </a><br/>
<a href = "https://gldmg.tistory.com/142"><i>딥러닝 메모장, anaconda SSL 오류 해결</i> </a><br/>
