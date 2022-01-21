---
layout: post
title: "[Git] Git, Github and basic function of Git"
date: 2022-01-21 19:20:23 +0900
category: Git
---
<font size = "5"><b>1. What is 'Git' and 'Github'?</b></font>
<hr style="border: solid 0.1px black;">
<center><img src = "https://user-images.githubusercontent.com/80208196/150519742-4c9df8d8-e114-47c6-a606-e5af17789b7b.jpg" width="500" height="250"></center>
&nbsp;&nbsp;<b><I>Git</I></b> is the instrument for verscion control and mangement of source code. You can check the version by <I>history</I> of Git and revise code or fix errors. Moreover, It is useful for collaborating with others. You can merge the work others did. Also, you can check and confirm who, when, what part of your project is created or revised. At the same time, Git even automatically checks any differences added by anyone else. It prevents any work getting deleted or harmed by other works. But Git only compares the works done using languages or tools basically set. If you want to automatically check by Git the difference of works done using Microsoft words, images and etc, you have to set some options. Otherwise, you can only check the difference of the size of files.<br/><br/>
&nbsp;&nbsp;<I><b>Github</b></I> is the service including the remote repository of Git and the community for developers. Github serves the remote repository of the project by using Git. You can manage your projects by the repository in internet and the functions you have to develop using <I>Issues</I>. Github also serve some functions like SNS for developers. You can search some open-source project and technologies you are interested in. Moreover, you can contribute some projects if you want.<br/><br/>

<br/>
<font size = "5"><b>2. What is 'commit'?</b></font>
<hr style="border: solid 0.1px black;">
<center><img src = "https://user-images.githubusercontent.com/80208196/150516516-2b081a79-bd8e-4251-8867-d62e09f2fae9.PNG" width="500" height="300"></center>
&nbsp;&nbsp;Git is version control using <b><I>Commit</I></b>. Commit is the current status of project. Commit stores some information like snapshot including <b>'Who commit', 'When commit' and the status of project</b> including information of what is revised.
<br/>
<center><img src = "https://user-images.githubusercontent.com/80208196/150547875-89f8089d-d4c5-4915-839f-24a31fc56353.png" width="500" height="200"></center>
&nbsp;&nbsp;If you want to commit your local files, you have to add your local files on 'Stage'. You can do this using command <I>"git add"</I>. <b>Git ONLY commits the files of which status is 'Staged'</b>. It prevents you from commiting some files not related with your project, some files of which size is too large or some files which threaten the security of your project.

> &nbsp;&nbsp;Also, There is another way to adjust which file to commit. Make a text file and name the file <b>'.gitignore'</b>. Just write the name of file at '.gitignore' if you don't want to commit that. You can use this way not to commit modules, folders and filename extensions.

&nbsp;&nbsp;You will add your local files on <I>Stage<I> to commit them. You can check what files you add or any files revised or created using command <I>"git status"</I>. After you add your local files and check the files are 'Staged', you can commit the files using command <I>"git commmit"</I>.


<br/>
<font size = "3"><b>References</b></font>
<a href="https://play.google.com/store/apps/details?id=com.FMasters.dbzindev"><font size = "2">1. "[Git] .gitigore이란? / .gitignore 사용법", 개발자 아저씨들 힘을모아</font></a>


<center><font size = "2"><span style = "opacity:0.5">This post is based on <I>git class</I> of <I>Sparta Coding Club</I>.</span></font></center>
<br/><br/>