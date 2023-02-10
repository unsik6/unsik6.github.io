---
layout: post
title: Segment Tree
subtitle: Tree to solve Range Query
categories: [Data Structures]
tags: [Data Structures, Algorithms, Tree, RMQ, C++]
---
## 1. Segment Tree
<hr>
&nbsp;&nbsp;<i>Segment Tree</i> is a data structure to solve queries about range(e.g. RMQ, Prefix Sum). Segment Tree is often used when people solve problems of Online Judges or coding tests of recruitment process of companies.

<img src = "https://user-images.githubusercontent.com/80208196/217886781-a96f3d7e-9d08-4d3d-a8ae-4b8ff142b9a5.png"><center><span style = "opacity:0.5">fig 1. Segment Tree for Prefix Sum Query</span></center><br/>

<b>Topologies</b>

- $I$ is whole interval of given data.
- $T$ is the segment tree which correspond to $I$.

<b>Properties</b>

- Leaves of $T$ correspond to each element of $I$. The leftmost leaf correspond to the leftmost element of $I$. The left-right sequence of logical position of leaves is same with the sequence of elements.
- A internal node $n$ of $T$ correspond to intervals that start from the element $s$ to $e$. $s$ correspond to the leftmost leaf of the subtree rooted by the $n$, and $e$ correspond to the rightmost leaf of the subtree rooted by the $n$. <u><b>That is, all subtree of $T$ is a segment tree, recursively.</b></u>
- Each node stores the value of the query for the interval(range, segment) which correspond to itself.

<br/>
&nbsp;&nbsp;There are three operations, <i>Build, Query, Update</i>. I will implement the operations of a segment tree implemented using a array.

<br/><br/>

## 2. Build
<hr>
&nbsp;&nbsp;Building Segment Tree is similar with <i>Merge Sort</i>. Run the process below, recursively.

- Input is the start index $s$ and the end index $e$ of the interval.
1. (Base case) If $s$ and $e$ are the same, it is a leaf. Store $A[s]$ at the node.
2. Else, divide the input interval $[s..e]$ to $[s..(s+e)/2]$ and $[(s+e)/2+1..e]$.
3. Run this process of the divided intervals, recursively.
4. Sum the values stored left child and right child. The children is already built and store by recursion of the third stage.

### Time Complexity
&nbsp;&nbsp;The time complexity of <i>Build</i> operation is $O(N \log{N})$, where $N$ is the number of elements. The height of the segment tree is $\lceil \log{N} \rceil$. And there are $O(N)$ <i>sum</i> operation per level.

### Source Code

<script src="https://gist.github.com/unsik6/404205df9c6cd43f1d8bd9627b0e45b7.js"></script>

- If you use a static array, make a array of size $4N$. Because a segment tree is a full binary tree whose height is $\lceil \log{N} \rceil$, the upper bound of the size of a segment tree is derived by $$\sum_{i=0}^{\lceil \log{N} \rceil}{2^i} < 2^{\lceil \log{N} \rceil + 1} - 1 < 4N$$

<br/><br/>

## 3. Query
<hr>

<img src = "https://user-images.githubusercontent.com/80208196/217905040-2c0059df-92bf-4959-b952-3c06b46a834d.png"><center><span style = "opacity:0.5">fig 2. Visited nodes in <i>Query</i> for $A[1..3]$</span></center><br/>

&nbsp;&nbsp;Using a segment tree, we can find the answer of queries in $O(\log{N})$ time by traveling a segment tree recursively.

1. Case 1: The interval of the current node is not in the interval of the query. Return null value.
2. Case 2: The interval of the current node is in the interval of the query. Return the value of the query stored in the node.
3. Case 3: The some elements of interval of the current node is in the interval of the query, but the rest of them is not in. Run the query on the subtrees rooted by children of the current node. After that, return sum of the result of the queries.

### Time Complexity
&nbsp;&nbsp;The time complexity of <i>Query</i> operation is $O(\log{N})$. In the worst case, The process above is runned recursivey until reaching to leaf. Note that at most 2 leaves will be visited. If <i>Case 3</i> occurs, it means the interval of the node hang over the boundary of the interval of the query. So, after division the interval of the query, the interval of one child may still hang over the boundary, but another is in the interval of the query. Because there are two boundaries, the process is runned recursively until reaching to leaf only twice. Moreover, the process about another child is never runned more than 1 time, because the interval of the child is fully in the interval of the query. The height of a segment tree is $\lceil \log{N} \rceil$.

### Source Code

<script src="https://gist.github.com/unsik6/67af4c420b9da2b01f269efd5818c5bc.js"></script>

<br/><br/>

## 2. Update
<hr>

<img src = "https://user-images.githubusercontent.com/80208196/217912410-79b0b3db-ce4f-43c5-aafc-0bfe835ee122.png"><center><span style = "opacity:0.5">fig 3. The nodes whose query value is changed, when $A[1]$ is changed</span></center><br/>

&nbsp;&nbsp;If you want to change element $A[i]$, <i>Update</i> operation changes the query values stored in all related nodes. It is possible by traveling a segment tree recursively.

1. (Base case: A) If the current node is a leaf(It must correspond to $A[i..i]=A[i]$), change the value of the leaf.
2. (Base case: B) If the interval that correspond to the current node does not include $i$, do nothing.
3. If the interval that correspond to a child, run recursively this process to the child. After that, recompute the query value of the current node.

&nbsp;&nbsp;This operation can be changed more simple using $diff = A'[i] - A[i]$, $A'[i]$ is new element.

1. Add $diff$ to the value of the current node.
3. If the current node is an internal node, run recursively this process to the child which correspond to the interval that includes $i$.

### Time Complexity
&nbsp;&nbsp;There is no branch, so the time complexity of <i>Update</i> is $O(\log{N})$.

### Source Code

<script src="https://gist.github.com/unsik6/0a0c04579d93cbda3224f4c3189c556f.js"></script>

<br/><br/>

## Refers
<hr/>
<a href = "https://yoongrammer.tistory.com/103">yoongrammer, "세그먼트 트리(Segment Tree) 개념 및 구현"</a><br/>
<a href = "https://stackoverflow.com/questions/30236813/segment-tree-query-complexity">stack overflow, "Segment tree - query complexity"</a><br/>