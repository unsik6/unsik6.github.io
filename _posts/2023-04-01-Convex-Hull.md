---
layout: post
title: Convex Hull algorithm (feat. BOJ 1708)
subtitle: BOJ Platinum 5
categories: Algorithms
tags: [BOJ, Algorithms, Geometry, C++]
---
## 1. Problem
<hr>
&nbsp;&nbsp;BOJ_1708 is the convex hull problems solved by <i>Convex Hull algorithm</i>. The levels of problem are <span style="color:#33ffcc">Platinum 5</span>.<a href="https://www.acmicpc.net/problem/1708">(Link of the problem of BOJ)</a><br/>

<b><i>Inputs</i></b>
- The number of the points $N (3\leq N \leq 100,000)$
- x-coordinate and y-coordinate of points $\| x\|, \| y\| \leq 40,000 $

<b><i>Outputs</i></b>
- The number of points of the convex hull covering all input points.

<b><i>Time & Space Limit</i></b>
- Time limit: 2 sec
- Space limit: 128 MB

<br/><br/>

## 2. Convex Hull Algorithms
<hr>
<img src = "https://user-images.githubusercontent.com/80208196/229359178-503a8a13-89dc-45cd-90b6-bcb096dfe8e0.png"><center><span style = "opacity:0.5">Fig 1. Convex, Convex Hull</span></center><br/>

&nbsp;&nbsp;<i><b>Convex</b></i> is a subset $S$ of the plane if and only if for any pair of points $p, q \in S$ the line segment $\overline{pq}$ is completely contained in $S$. In the Fig 1., the left yellow plane is not convex, since the left black line between two points is not included in the plane. On the contrary, the right yellow plane is the convex of $S$. <i><b>Convex Hull</b></i> of $S$ is the smallest convex set that contains $S$.<br/>

### Naive Algorithm

<img src = "https://user-images.githubusercontent.com/80208196/229359541-1bd44c93-890e-4c91-b6fe-5d4ee9e01752.png"><center><span style = "opacity:0.5">Fig 2. The upper lines and lower lines of the convex hull</span></center><br/>

&nbsp;&nbsp;Think about the upper lines of the convex hull. If upper lines start from left, then the direction of the lines is from left to right. And, <u>all points of $S$ except the points on the upper line have to be right side of upper lines.</u> So, check the each pssible line whether all points are on the right side of that. When checking whether a point is on the left side or the right side of a line, use <a href = "https://unsik6.github.io/algorithms/2023/03/26/CCW.html"><i>CCW algorithm</i></a>. If the result of the algorithm is negative, then a point is on the left side of a line, else on the right side. About the lower lines, do same process reverse.<br/> Sadly, its running time is $O(N^3)$.<br/>

### With Sorting the points

<img src = "https://user-images.githubusercontent.com/80208196/229367452-9300a37d-36a9-4608-9678-f5301508da98.png"><center><span style = "opacity:0.5">Fig 3. an example of the process, when checking the $i$th point</span></center><br/>

&nbsp;&nbsp;To optimize this algorithm, we sort the points left to right. By sorting the points of $S$ in increasing order according to x-coordinate(if points are on the same vertical slab, sort in increasing order according to y-coordinate), we can scan points from left to right. If the sequence of the points is $p_1, p_2, ... ,p_N$ in lexicographic order, check the points one by one whether the each point is on the line of the convex hull. If we compute the points on the upper lines, $p_1, ... p_{i-1}$ is the sequence of the points on the upper lines before considering the $i$th point. If $p_i$ is on the left side of the line $\overline{p_{i-2}p_{i-1}}$, the line $\overline{p_{i-2}p_{i-1}}$ is not on the upper lines of the convex hull. Then, drop out the $p_{i-1}$, and check iteratively the line $\overline{p_{i-3}p_{i-2}}$. Else, $p_i$ is the point on the upper lines(until it will be dropped). For referring the points, use the stack consisting of the points on the line of convex hull.<br/>

<img src = "https://user-images.githubusercontent.com/80208196/229367452-9300a37d-36a9-4608-9678-f5301508da98.png"><center><span style = "opacity:0.5">Fig 4. the degenerate case</span></center><br/>

&nbsp;&nbsp;Since points are already sorted in increasing order according to x-coordinate, the direction of $\overline{p_{i-1}p_i}$ is always from left to right. Furtheremore, it is important to sort the points, whose x-coordinate is same, in increasing order according to y-coordinate. As you can see in Fig 4., if the last accessed point is the last point in each order, using below one(descending order acoording to y-coordinate) cannot drop the last point which is not the point of the convex hull. Focus on that we have to keep the property, "The points not of the convex hull have to be on the left side of the last edge we consider.<br/>
&nbsp;&nbsp;Time complexity of this algorithm is $O(nlog{n})$. It depends on the preprocessing(points sorting). In main process, each point is checked only one time in linear traversal. And, each points can be dropped only one time. So, running time of main process is $O(n)$.

### Optimization

<img src = "https://user-images.githubusercontent.com/80208196/229369468-33efce00-7b92-4095-8a9c-923cb1b25d96.png"><center><span style = "opacity:0.5">Fig 5. The sequence of the points in descending order according to CCW for the pivot.</span></center><br/>

&nbsp;&nbsp;The above way to compute the convex hull need to compute upper lines and lower lines respectively. It does not affect the total time complexity of the algorithm, but we have to operate the process twice. We can reduce running time by running the process only one time. For this, the points are sorted in descending order according to CCW for the point $p_{pivot}$. $p_{pivot}$ is the lowest and leftmost point. Descending order according to CCW for $p_{pivot}$ is similar with the order of the outermost. If CCW of points is same, then sort the points in descending order according to y-coordinate. And, run same process above with checking whether $p_i$ is on left side. It makes the lines of the convex hull rotating counterclockwise. As you can see in Fig 5., $p_i$ does not exist behind the direction of $\overline{p_{i-2}p_{i-1}}$. The ccw of some points for the pivot can be same. For handling this degenerate case, the points have to be sorted in increasing order according to the distance with the pivot. Think the dash line of Fig 5 like a vertical slab in Fig 4. Then you can understand why the order is chosen.<br/><br/>

### Psuedocode

<b>Input</b> A set $P$ of points in the plane $S$ <br/>
<b>Output</b> A list containing the points of the convex hull of $S$<br/>
$pivot \leftarrow the lowest and leftmost point$<br/>
Sort the points in descending order according to CCW for $pivot$.<br/>
$stk \leftarrow \text{empty stack}$<br/>
$stk.push(p_1); stk.push(p_2)$<br/>
$i \leftarrow 3$<br/>
<b>while</b> $i \leq N$ <b>do</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;<b>while</b> not $stk.empty()$ <b>do</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;$p_{i-1} \leftarrow stk.top(); stk.pop()$<br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;$p_{i-2} \leftarrow stk.top();$<br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>if</b> ccw between $p_i$ and $\overline{p_{i-2}p_{i-1}} > 0$<br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;$stk.push(p_{i-1}); break$<br/>
&nbsp; &nbsp; &nbsp; &nbsp;$stk.push(p_i)$<br/>
<b>return</b> elements of $stk$<br/>

<br/><br/>

## 3. Source code
<hr>
<script src="https://gist.github.com/unsik6/4226cab389fc49efc395481c0acc9164.js"></script>


<br/><br/>

## Refers
<hr/>
<a href = "https://link.springer.com/book/10.1007/978-3-540-77974-2">Mark Berg, Otfried Cheong, Marc Kreveld, Mark Overmars, "Computational Geometry: Algorithms and applications 3<sup>rd</sup>"</a><br/>
<a href = "https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=rbdud96&logNo=221516203360">rbdud96, "문제 해결 기법 - 11일차 - 계산 기하 - Convex Hull, Graham scan, Quick Hull"</a><br/>