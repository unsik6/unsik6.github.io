---
layout: post
title: GitBlog) Favicon
categories: GitBlog
tags: [GitBlog, Favicon, Yat]
published: true
---
## 1. Favicon
<hr>
&nbsp;&nbsp;Favicon is main icon of your git blog. If you set yout favicon, then you can see what like the pic below.
<center><img src = "https://user-images.githubusercontent.com/80208196/212710205-54fcbd64-31d8-4544-8a06-eb1eada21691.png"></center>

## 2. How to set a favicon
<hr>
&nbsp;&nbsp;First, I am using the jekyll theme, <a href = "https://github.com/jeffreytse/jekyll-theme-yat">'Yat'</a>. So, What I introduce in this section is only applied to the same theme.<br/><br/>
1. Prepare an image that you want to set for your favicon.<br/><br/>
2. Go to <a href = "https://realfavicongenerator.net/">realfavicongenerator</a>.<br/><br/>
3. Upload your image. Click 'Select your Favicon Image'. <center><img src = "https://user-images.githubusercontent.com/80208196/212711525-96ff5f49-c1eb-4d9e-a28e-ee58c6e84388.png"></center><br/>
4. Downlaod your package. Click 'Favicon package' in the image below. Now, you get a zip file.<center><img src = "https://user-images.githubusercontent.com/80208196/212730911-06746699-2558-4218-a3e0-226f1c82145e.png"></center><br/>
5. Decompress the zip file. Rename the file decompressed to 'favicon.ico'.<br/><br/>
6. Move the file into 'assets' folder.<br/><br/>
7. Copy the code in the image above. And, paste that at `/_includes/custom_head.html`. You have to copy the relative path of 'favicon.ico' folder, and paste that at the `{folder_path}` in the code below.
    <script src="https://gist.github.com/unsik6/17bdce4d46bd9cf6b99892eccda74078.js"></script>

8. Go to '_config.yml', and set the relative path of 'favicon.ico' <u>file</u> in the 'favicon.ico' <u>folder</u> the value of `favicon`.
    <center><img src = "https://user-images.githubusercontent.com/80208196/215963864-4033402e-df35-4bd7-affc-7bb078c695ea.png"></center>