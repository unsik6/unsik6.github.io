---
layout: post
title: Floyd-Warshall algorithm (feat. BOJ 1602)
subtitle: BOJ Platinum 4
categories: Algorithms
tags: [BOJ, Algorithms, Shortest Path, Floyd-Warshall, C++]
---
## 1. Problem
<hr>
&nbsp;&nbsp;BOJ_1602 is the problem solved by <i>Floyd-Warshall algorithm</i>. The level of problem is <span style="color:#33ffcc">Platinum 4</span>.<a href="https://www.acmicpc.net/problem/1602">(Link of the problem of BOJ)</a><br/>

<b><i>Inputs</i></b>
- The number of cities $N (2 \leq N \leq 500)$
- The number of roads $M (0 \leq M \leq 10,000)$
- The number of queries $Q (0 \leq Q \leq 40,000)$
- $N$ rows: The time $t$ for the dog to bully cat in city $i\; (1 \leq i \leq N, 1 \leq t \leq 10,000$
- $M$ rows: Two cities $a$, $b$ connected by a road and the time $d$ the cat takes to pass the road $(1 \leq a, b \leq N, 1 \leq d \leq 10,000)$
- $Q$ rows: start city $S$ and destination city $T\; (1 \leq S, T \leq N)$

<b><i>Conditions</i></b>
- The dog wait the cat at a city where the dog can tease the cat as possible as long. The city is one of the city cat will pass.
- The weight of the path is the time it takes to pass through all the roads that make up the path plus the time it takes for the dog to bully the cat.

<b><i>Outputs</i></b>
- For each queries, the minimum time it takes for the cat to run from city $S$ to city $E$. If there is no path between the cities, the output of a query is $-1$.

<b><i>Time & Space Limit</i></b>
- Time limit: 2 sec
- Space limit: 128MB

<br/><br/>

## 2. Approach to the problem
<hr>

&nbsp;&nbsp;If we compute the shortest path for each query and the query time is $q$, then it takes $O(qQ)$ time to solve the problem. In the worst case, $Q$ is $40,000$. Assuming that it takes a second to execute 100,000,000 primitive opeartions, $q$ has to be less than 5,000. If we use <i>Dijkstra's algorithm</i>, a single-source shortest path algorithm, then $q$ is $O((N+M)\log{M})$. In the worst case, it is $O(50,000 \times 14)$. Therefore, we can not choose the solution.<br/>
&nbsp;&nbsp;Note that the number of vertices is very small and there are so many queries. Using the query whose running time is very short and preprocessing time which depends on the number of vertices may be best. Therefore, we will use <i><b>Floyd-Warshall algorithm</b></i> whose running time is constant and preprocessing time is $O(N^3)$.

<br/><br/>

## 3. Floyd-Warshall Alogorithm
<hr>

&nbsp;&nbsp;<i><b>Floyd-Warshall algorithm (WFI algorithm)</b></i> is an algorithm for finding all-pair shortest paths(APSP) in a directed weighthed graph. But, there is no negative cycle in a given digraph.

### 1) APSP
&nbsp;&nbsp;There is four types of shortest path problem.

1. Single-Source Shortest Path (SSSP):
    - Input: a graph and a vertex
    - Output: All shortest paths from a given vertex to all vertices
    <br/><br/>
2. Single-Destination Shortest Path (SDSP):
    - Input: a graph and a vertex
    - Output: All shortest paths from all vertices to a given vertex
    > Note: SDSP is same with SSSP. In an undirected graph, the solution of SDSP is solving SSSP with a given vertex of SDSP as the source. In a digraph, transpose all edges befor solving SSSP with a given vertex of SDSP as the source.
    <br/>
3. Singe-Pair Shortest Path (SPSP):
    - Input: a graph and two vertices (source, destination)
    - Output: a shortest path from a source to a destination
    > Note: SPSP is same with SSSP. Because a shortest path can be decomposed as shortest paths from a source to other vertices or from other vertices to a destination, we can know whether a path is a shortest path or not after computing shortest paths from a source to all vertices.
    <br/>
4. <b>All-Pair Shortest Path (APSP)</b>:
    - Input: a graph
    - Output: all shortest path of all pair of vertices

&nbsp;&nbsp;We can solve APSP by running an algorithm for solving SSSP repeatedly by the number of vertices. Set each vertex as a source of SSSP. If using Dijkstra's algorithm, It takes $O((N^2+NM)\log{M})$ time to solve APSP. If a given graph is spars, the time complexity is $O(N^2 \log{N})$. But if a given graph is dense, the time complexity is $O(N^3 \log{N})$.

<br/>

### 2) Algorithm

&nbsp;&nbsp;WFI algorithm considers the intermediate vertices of a shortest path. If a simple path $p$ is $<v_1, v_2, ... v_l>$, any intermediate veritex is in the set $\\{ v_2,...,v_{i-1} \\}$. WFI algorithm builds the two dimensional matrix $M_k$ with dynamic programming, where $M_k[i][j]$ is the weight of a shortest path from vertices labeld $i$ and $j$(vertex $i$ and vertex $j$) with considering its intermediate vertices in the set $\\{1, 2, ..., k\\}$. Therefore, Elements of $M_N$ is the weights of shortest paths. Because $M_k$ is constructed by using $M_{k-1}$, $M_N$ is recursively constructed.

$$
M_k[i][j] = 
\begin{cases}
M_{k-1}[i][j], & \text{if $M_{k-1}[i][j] \leq M_{k-1}[i][k] + M_{k-1}[k][j]$} \\ 
M_{k-1}[i][k] + M_{k-1}[k][j], & \text{if $M_{k-1}[i][j] > M_{k-1}[i][k] + M_{k-1}[k][j]$}
\end{cases}
$$

&nbsp;&nbsp;This algorithm is correct, because considering all intermediate vertices. If vertex $k$ is not in a shortest path from vertex $i$ to vertex $j$, the intermediate vertices of a shortest path from vertex $i$ to vertex $j$ are in the set ${1,2,...,k-1}$. ($M_k[i][j] = M_{k-1}[i][j]$) Else, $M_k[i][j]$ can be decomposed to a shortest path $p_1$ from vertex $i$ to vertex $k$ and a shortest path $p_2$ from vertex $k$ to vertex $j$. Vertex $k$ is the destination of $p_1$ and the source of $p_2$, so vertex $k$ is not an intermediate vertex of $p_1$ and $p_2$. So, the intermediate vertices of $p_1$ and $p_2$ are in the set ${1,2,...,k-1}$. ($M_k[i][j] = M_{k-1}[i][k]+M_{k-1}[k][j]$)
&nbsp;&nbsp;Because we have to consider all vertices as an intermediate vertex, the algorithm constructs $M_N$ from $M_0 = \text{a given graph}$.
&nbsp;&nbsp;$M_N$ does not store <i>a shortest path</i> but the weight of a shortest path. We can construct a shortest path by storing a shortest path in a $N \times N$ matrix $MP$. If $M_{k}[i][j]$ is $M_{k-1}[i][k]+M_{k-1}[k][j]$, a shortest path in $MP[i][j]$ is $MP[i][k] + MP[k][j]$. Alternatively, we construct a new matrix for each stage that construct $M_k$, and store a vertex that comes before vertex $j$ in a shortest path from vertex $i$ to vertex $j$.

<br/><img src = "https://user-images.githubusercontent.com/80208196/218610439-933d939c-a9e1-489d-a0a2-da8cf7bf51c1.gif"><center><span style = "opacity:0.5">fig 1. Floyd-Warshall algorithm by <a href = "https://velog.io/@codesver/til-algorithm-floyd-warshall-230131">codesver</a></span></center><br/>

### 3) Complexity

- Time Complexity: $O(N^3)$
- Space Complexity: $O(N^2)$

&nbsp;&nbsp;We have to compute $N^2$ paths in each stage. And we have to consider all vertices as an intermediate vertex. Finally, the time complexity of the algorithm is $O(N^3)$.<br/>
&nbsp;&nbsp;If we update $M_{k-1}$ to $M_k$ instead of creating $M_k$, then the space complexity of the algorithm is $O(N^2)$.

### 4) Psuedocode

<b>Input</b> graph $G$ <br/>
<b>Output</b> matrix $M$, where $M[i][j]$ is the weight of a shortest path from vertex $i$ to vertex $j$<br/>
<b>for</b> $i = 1$ <b>to</b> $N$ <br/>
&nbsp; &nbsp; &nbsp; &nbsp;<b>for</b> $j = 1$ <b>to</b> $N$ <br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>if</b> $i \neq j$ <b>then</b> <br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;$M[i][j] = \infty$<br/>
<b>for</b> $k = 1$ <b>to</b> $N$ <br/>
&nbsp; &nbsp; &nbsp; &nbsp;<b>for</b> $i = 1$ <b>to</b> $N$ <br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>if</b> $i \neq k$ <b>then</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>continue</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>for</b> $j = 1$ <b>to</b> $N$ <br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>if</b> $j \neq i$ <b>or</b> $j \neq k$ <b>then</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>continue</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;<b>if</b> $M[i][j] \geq M[i][k] + M[k][j]$ <b>then</b><br/>
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;$M[i][j] \leftarrow M[i][k] + M[k][j]$


<br/><br/>

## 4. Apply WFI algorithm to the problem
<hr>

&nbsp;&nbsp;The problem of BOJ 1602 can be solved using WFI algorithm. Cities correspond to vertices and roads correspond to edges. However, we have to consider the weight of a vertex, the time it takes for the dog to bully the cat. $t_v$ is the time it takes for the dog to bully the cat in city $v$. The dog waits the cat in the city $v$, if $t_v$ is the maximum among vertices in path $p$ from city $i$ to city $j$.

$$
t_{i j} = max(t_v : v \in \text{path from city $i$ to city $j$})
$$

&nbsp;&nbsp;The sum of weights of a path from city $i$ to city $j$ is stored $SR_{ij}$. $cost_{ij}$ is the total weight of a shortest path from city $i$ to city $j$. $cost_{ij} is,

$$
cost_{ij} = SR_{ij} + t_{ij}
$$

&nbsp;&nbsp;Because WFI algorithm considers all vertices as an intermediate vertex, we can check all path from city $i$ to city $j$ if we apply the formula above to WFI algorithm. $cost_{ij}^{k}$ is the minimum cost of paths from city $i$ to city $j$ whose intermediate vertices are in the set $\\{1,2,...,k\\}$.

$$
\begin{align}
& originCost = cost_{ij}^{k-1} \\  
& withKCost = SR_{ik} + SR_{kj} + max(t_{ik}, t_{kj}) \\ & cost_{ij}^{k} = 
\begin{cases}
originCost, & \text{if $originCost \leq withKCost$} \\ 
withKCost, & \text{if $originCost > withKCost$}
\end{cases} \\ \end{align}
$$

&nbsp;&nbsp;To execute the recursion above, we store $SR$ and $t_{ij}$ in different matrices.<br/>
&nbsp;&nbsp;However, we can not apply the formula above to WFI algorithm directly. If the order of considering intermediate vertices is the same as the WFI algorithm, $cost_{ij}^{N}$ is not guaranteed to be minimal. The main property of WFI algorithm is that $cost_{ij}^{k}$ is a shortest path from vertex $i$ and vertex $j$, considering vertices in the set $\\{1, 2, ..., k\\}$. By the formula above, $cost_{ij}$ consist of $SR_{ij}$ and $t_{ij}$. So checking from both elements are minimal is best way to find the minimum. The $SR_{ij}$ must be affected when new vertex is considered as an intermediate vertex. But, it doesn't follow $t_{ij}$ is affected, becuase $t_v$ where $v$ is new node is ignored original $t_{ij}$ is greater. Therefore, run WFI algorithm in the increasing order of $t_v$. Because <b><u>the order of considering intermediate vertices is no matter in original WFI algorithm</u></b>, the changed order does not affect correctness.

<br/><br/>

## 5. Source Code
<hr>

<script src="https://gist.github.com/unsik6/76151aa3b04ecef12f21fef3e96c0854.js"></script>

<br/><br/>

## Refers
<hr/>
<a href = "https://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844">Thomas H. Cornen, Charlse E. Leiserson, Ronald L. Rivest, Clifford Stein, "Introduction to Algorithms 3<sup>rd</sup>"</a><br/>
<a href = "https://velog.io/@codesver/til-algorithm-floyd-warshall-230131">codesver, "[ TIL ] Floyd Warshall"</a><br/>
<a href = "https://steady-coding.tistory.com/107">제이온, "[BOJ] 백준 1602번 : 도망자 원숭이 (JAVA)"</a><br/>
<a href = "https://www.acmicpc.net/board/view/8589">sksdong1, "풀긴 풀었는데요.."</a><br/>