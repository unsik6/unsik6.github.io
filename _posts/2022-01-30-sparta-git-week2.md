---
layout: post
title: "[Git] Collaborate using Git, 'Issue', 'Branch', 'Merge'"
date: 2022-01-22 03:37:00 +0900
category: Git
---

<center>
        <table border ="1" width = "300">
            <tr>
                <td>
                <a href = "#1"><font size = "2">&nbsp;&nbsp;1. What is 'Issue'?</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#2"><font size = "2">&nbsp;&nbsp;2. What is 'Branch' and 'Merge'?</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#3"><font size = "2">&nbsp;&nbsp;3. How to manage 'Merge Conflict'?</font></a>
                </td>
            </tr>
        </table>
</center>
<br/><br/>

<p id = "1"><font size = "5"><b>1. What is 'Issue'?</b></font></p>
<hr style="border: solid 0.1px black;">
<center><img src = "https://user-images.githubusercontent.com/80208196/151689436-019d9014-2566-45c9-ad01-684e22c5673d.PNG" width="300" height="200">&nbsp;<img src = "https://user-images.githubusercontent.com/80208196/151689437-11cd5c48-aac5-4d3a-80d2-5d8085be918c.PNG" width="100" height="200"></center>
<center><font size = "2"><span style = "opacity:0.5">Left is the web page, 'Create Issue' and Right is the part of the labels of Issue.</span></font></center>
&nbsp;&nbsp;<I><b>'Issue'</b></I> is the function of GitHub for managing the project or repository. You can select the assignee who will do the work of Issue and select the labels that make all collaboraters can easily check what about the issue. also, You can select the project that ths issue is included in. There are a number of labels you can select. And you can make the labels that you want. After you open new issue, you can check the issue number beside the name of issue.

<br/><br/>
<center><img src = "https://user-images.githubusercontent.com/80208196/151689513-15d9de81-8c43-45a8-a04d-b2d3129120a5.PNG" width="300" height="200"></center>
&nbsp;&nbsp;You can discuss with your collaobraters about ths issue opened. And, If you push your commit named as <I>"(commit name) #(issue number)"</I>, the commit automatically register in the timeline of the issue. If the issue is completeed, <I>Close</I> the issue. Whenever you want to open the issue, you can reopen that.


<br/><br/>
<p id = "2"><font size = "5"><b>2. What is 'Branch' and 'Merge'?</b></font>
<hr style="border: solid 0.1px black;"></p>
<center><img src = "https://user-images.githubusercontent.com/80208196/151693431-8594446d-0b19-4de3-8b2b-efb16e3370cc.PNG" width="600" height="200"></center>
<center><font size = "2"><span style = "opacity:0.5">Branch Graph and Commit History (in <I>SourceTree</I>, one of GitHub GUI)</span></font></center>
&nbsp;&nbsp;<I><b>Branch</b></I> is the useful tool for collaboration. You can create a new branch at any commit you want. Branch is independent work place others including main branch. <I>'Checkout'</I> means change your Work-Tree to the branch. If you checkout the branch, you can work with other branches not affected.
<br/>&nbsp;&nbsp;You can manage branches. Create new one, initialize one and delete one. You have to checkout other branch that is not the branch you want to delete. If you delete a branch, the all commits of the branch is deleted.
<br/>

> The local repository is tracking the remote repository in each branch unit. In the local repository, you can check how much different with the branch of the remote repository.


&nbsp;&nbsp;When you complete your work on the branch, you have to merge your branch with another. <I><b>'Merge'</b></I> is reflection the commits of the branch to the checkout branch you want. Commonly, Project have the <I>flow</I> ,the rule of management of branches including how to commit and work. There are some representative flows called <I>'Git Flow', 'GitHub Flow' and 'GitLab Flow'</I>. You can check them at reference of this post. (I will post about flow soon.)
<br/>
&nbsp;&nbsp;You can select some style when you merge branches. First, you can immediately merge your branches or not. Second, you can create commit recording merge. If the merge is <I>fast-foward</I> merge, you can merge without creating a merge commit. 'Fast-foward' is the relation of branches. The branch don't make conflicts and just follow other branches. In that case, It is called fast-foward relation. Of course, you can create the merge commit when you merge the branches in fast-foward relation.


<br/><br/>
<p id = "3"><font size = "5"><b>3. How to manage 'Merge Conflict'?</b></font>
<hr style="border: solid 0.1px black;"></p>
<center><img src = "https://user-images.githubusercontent.com/80208196/151696240-f02c6960-b49b-4751-807d-d28cbd6ab46c.PNG" width="300" height="100"></center>
<center><font size = "2"><span style = "opacity:0.5">The commits after the commit 'Merge branch', include revision of the same file. It will make the Merge conflict.</span></font></center>
&nbsp;&nbsp;If you and your co-workers work at same file in each branch, <I><b>Merge Conflict</b></I> will occur when your team try merging the branches. In that case, GitHub doesn't merge your branches with Merge Conflict and notice you have to solve the conflict.
<br/><br/>

<center><img src = "https://user-images.githubusercontent.com/80208196/151696689-9e85db1e-8dfc-4ab9-b481-e982f0d0732c.PNG" width="200" height="140"></center>
<center><font size = "2"><span style = "opacity:0.5">GitHub give you the files which casue Merge Conflict like that.</span></font></center>
&nbsp;&nbsp;Then, GitHub create new commit, only files which cause the conflict is staged. The files were revised like the picture above. Among the contents of files, "&lt;&lt;&lt;&lt;&lt;&lt;&lt;HEAD ~ &gt;&gt;&gt;&gt;&gt;&gt; (branchName)" must be revised. It include the content of one of branch which cause the conflict before "=======" and the content of another after "=======". After you revise the files, add the files and commit. Then, Finally the merge is completed.


<br/><br/><br/>
<font size = "3"><b>References</b></font>
<a href="https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues"><font size = "2">1. "About Issue", GitHub Docs</font></a><br/>
<a href="https://terry-some.tistory.com/93"><font size = "2">2. "GitHub를 활용한 이슈 관리", 데니의 Techlog</font></a><br/>
<a href="https://docs.github.com/en/get-started/quickstart/github-flow"><font size = "2">3. "GitHub Flow", GitHub Docs</font></a><br/>
<a href="https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/"><font size = "2">4. "Git flow, GitHub flow, GitLab flow", 잘 밤에 쓸데없는 생각하기</font></a><br/>

<br/><br/><center><font size = "2"><span style = "opacity:0.5">This post is based on <I>git class</I> of <I>Sparta Coding Club</I>.</span></font></center>
<br/><br/>