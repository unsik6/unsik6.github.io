---
layout: post
title: GitBlog) Favicon
categories: GitBlog
tags: [GitBlog, Favicon, Yat]
---
## 1. Favicon
<hr>
&nbsp;&nbsp;Favicon is main icon of your git blog. If you set yout favicon, then you can see what like the pic below.
<center><img src = "https://user-images.githubusercontent.com/80208196/212710205-54fcbd64-31d8-4544-8a06-eb1eada21691.png"></center>

## 2. How to set a favicon
<hr>
&nbsp;&nbsp;First, I am using the jekyll theme, <a href = "https://github.com/jeffreytse/jekyll-theme-yat">'Yat'</a>. So, What I introduce in this section is only applied to the same theme.<br/>
1. Prepare an image that you want to set for your favicon.
2. Go to <a href = "https://realfavicongenerator.net/">realfavicongenerator</a>.
3. Upload your image. Click 'Select your Favicon Image'. <center><img src = "https://user-images.githubusercontent.com/80208196/212711525-96ff5f49-c1eb-4d9e-a28e-ee58c6e84388.png"></center>
4. Downlaod your package. Click 'Favicon package' in the image below. Now, you get a zip file.<center><img src = "https://user-images.githubusercontent.com/80208196/212730911-06746699-2558-4218-a3e0-226f1c82145e.png"></center>
5. Decompress the zip file. Rename the file decompressed to 'favicon.ico'.
6. Move the file into 'assets' folder.
7. Copy the code in the image above. And, paste that at '/_includes/custom_head.html'. You have to copy the relative path of 'favicon.ico' folder, and paste that at the '{folder_path}' in the code below.

    ```html
    <link rel="apple-touch-icon" sizes="180x180" href="{folder_path}/apple-touch-icon.png">
    <link rel="icon" type="image/png" sizes="32x32" href="{folder_path}/favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="16x16" href="{folder_path}/favicon-16x16.png">
    <link rel="manifest" href="{folder_path}/site.webmanifest">
    <link rel="mask-icon" href="{folder_path}/safari-pinned-tab.svg" color="#5bbad5">
    <meta name="msapplication-TileColor" content="#da532c">
    <meta name="theme-color" content="#ffffff">
    ```
8. Go to '_config.yml', and set the relative path of 'favicon.ico' file in the 'favicon.ico' folder the value of 'favicon'.