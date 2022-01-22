---
layout: post
title: "[Git] Git, Github and basic function of Git"
date: 2022-01-22 03:37:00 +0900
category: Git
---

<center>
        <table border ="1" width = "300">
            <tr>
                <td>
                <a href = "#1"><font size = "2">&nbsp;&nbsp;1. What is 'Git' and 'Github'?</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#2"><font size = "2">&nbsp;&nbsp;2. What is 'commit'?</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#3"><font size = "2">&nbsp;&nbsp;3. What is 'repository'?</font></a>
                </td>
            </tr>
        </table>
</center>
<br/><br/>

<p id = "1"><font size = "5"><b>1. What is 'Git' and 'Github'?</b></font></p>
<hr style="border: solid 0.1px black;">
<center><img src = "https://user-images.githubusercontent.com/80208196/150519742-4c9df8d8-e114-47c6-a606-e5af17789b7b.jpg" width="500" height="250"></center>
&nbsp;&nbsp;<b><I>Git</I></b>, distributed reversion control system, is the instrument for verscion control and mangement of source code. You can check the version by <I>history</I> of Git and revise code or fix errors. Moreover, It is useful for collaborating with others. You can merge the work others did. Also, you can check and confirm who, when, what part of your project is created or revised. At the same time, Git even automatically checks any differences added by anyone else. It prevents any work getting deleted or harmed by other works. But Git only compares the works done using languages or tools basically set. If you want to automatically check by Git the difference of works done using Microsoft words, images and etc, you have to set some options. Otherwise, you can only check the difference of the size of files.<br/><br/>
&nbsp;&nbsp;<I><b>Github</b></I> is the service including the remote repository of Git and the community for developers. Github serves the remote repository of the project by using Git. You can manage your projects by the repository in internet and the functions you have to develop using <I>Issues</I>. Github also serve some functions like SNS for developers. You can search some open-source project and technologies you are interested in. Moreover, you can contribute some projects if you want.<br/><br/>

<br/>
<p id = "2"><font size = "5"><b>2. What is 'commit'?</b></font>
<hr style="border: solid 0.1px black;"></p>
<center><img src = "https://user-images.githubusercontent.com/80208196/150516516-2b081a79-bd8e-4251-8867-d62e09f2fae9.PNG" width="500" height="300"></center>
&nbsp;&nbsp;Git is version control using <b><I>Commit</I></b>. Commit is the current status of project. Committing snapshot of current status of your project stores some information including <b>'Who commit', 'When commit' and the status of project</b> including information of what is revised.
<br/>
<center><img src = "https://user-images.githubusercontent.com/80208196/150547875-89f8089d-d4c5-4915-839f-24a31fc56353.png" width="500" height="200"></center>
&nbsp;&nbsp;If you want to commit your local files, you have to add your local files on <I>'Staging area'</I>. You can do this using the command <I>"git add"</I>. <b>Git ONLY tracks and commits the files of which status is 'Staged'</b>. It prevents you from commiting some files not related with your project, some files of which size is too large or some files which threaten the security of your project.

> &nbsp;&nbsp;Also, There is another way to adjust which file to commit. Make a text file and name the file <b>'.gitignore'</b>. Just write the name of file at '.gitignore' if you don't want to commit that. You can use this way not to commit modules, folders and filename extensions.

<br/>
<center><img src = "https://user-images.githubusercontent.com/80208196/150566506-b4faf4b6-6ac6-443f-97cc-d0d2821997d7.PNG" width="500" height="200"><img src = "https://user-images.githubusercontent.com/80208196/150566511-8df6e5fd-ce14-46c3-9598-358ebd16b620.PNG" width="500" height="200"><img src = "https://user-images.githubusercontent.com/80208196/150566512-2b3ddf25-6788-4642-8d3a-893a52ff4ff2.PNG" width="500" height="100"></center>

&nbsp;&nbsp;You will add your local files on <I>Staging area</I> to commit them. You can check what files you added, revised or created using the command <I>"git status"</I>. After you add your local files and check the files are <I>'Staged'</I>, you can commit them using the command <I>"git commmit"</I>.<br/><br/>

<br/>
<p id = "3"><font size = "5"><b>3. What is 'repository'?</b></font>
<hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;There is two kind of <I><b>'Repository'</b></I>. <b>Local repository</b> is a project stored in only your computer data storage. <b>Remote repository</b> is a project stored in Git server on network like cloud service. You can connect local repository and remote repository. This is called <b>'Tracking'</b>. Local repository knows what remote repository to connect with, but remote repository doesn't know what local repository to connect with. And you already know that Git doesn't commit local repository automatically unlike cloud services.

<br/><center><img src = "https://user-images.githubusercontent.com/80208196/150580863-b61124c3-f2de-41c7-b5a1-a2dd11e23902.png" width="1000" height="200"></center>
<center><font size = "2"><span style = "opacity:0.5">by ref 2, 3</span></font></center>
&nbsp;&nbsp;You have to <I><b>'push'</b></I> commits to reflect the commits of local repository in remote repository using the command <I>"git push"</I>. On the contrary, You can reflect the commits of remote repository to local repository. This is done when you <I><b>'pull'</b></I> the commits of remote repository, using the command <I>"git pull 'remote repository name' 'branch name'"</I>. However, <I>Pull</I> includes merge. But if you don’t want to merge but still want to get the source code of the repository, use the command <I>"git fetch"</I>.
&nbsp;&nbsp;You can initialize a repository, using the command <I>"git init"</I>. And you can get remote repository, using the command <I>"git clone 'remote repository address"</I>.


<br/><br/><br/>
<font size = "3"><b>References</b></font>
<a href="https://programming119.tistory.com/105"><font size = "2">1. "[Git] .gitigore이란? / .gitignore 사용법", 개발자 아저씨들 힘을모아</font></a><br/>
<a href="https://sabarada.tistory.com/71"><font size = "2">2. "[git] git을 이용한 버전관리 - 기본편(add, commit, status, log, reset)", 사바라다는 차곡차곡</font></a><br/>
<a href="https://sabarada.tistory.com/75"><font size = "2">3. "[git] git을 이용한 버전관리 - 기본편 (remote, push, pull, fetch, clone) with github", 사바라다는 차곡차곡</font></a><br/>
<a href="https://git-scm.com/book/en/v2"><font size = "2">4. "Git - Pro book</font></a>


<br/><br/><center><font size = "2"><span style = "opacity:0.5">This post is based on <I>git class</I> of <I>Sparta Coding Club</I>.</span></font></center>
<br/><br/>