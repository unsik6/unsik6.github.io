---
layout: post
title: "[CLRS Review] Chapter 6. HeapSort"
date: 2022-02-05 01:30:00 +0900
category: CLRS_Review
---

<center>
        <table border ="1" width = "400">
            <tr>
                <td>
                <a href = "#1"><font size = "2">&nbsp;&nbsp;1. Heap</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#2"><font size = "2">&nbsp;&nbsp;2. How to keep Heap-Order with insertion and removal</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#3"><font size = "2">&nbsp;&nbsp;3. Build Heap</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#4"><font size = "2">&nbsp;&nbsp;4. Heap Sort</font></a>
                </td>
            </tr>
        </table>
</center>
<br/><br/>

<p id = "1"><font size = "5"><b>1. Heap</b></font></p>
<hr style="border: solid 0.1px black;">
<center><img src = "https://user-images.githubusercontent.com/80208196/159766086-98629d4c-033f-4807-b808-02d4d07bb6ea.PNG" width="600" height="500"><br/>
<font size = "2">Min-Heap</font></center>
&nbsp;&nbsp;<i><b>Heap</b></i> is a data structure implemented using a complete binary tree. In a heap, all nodes without root have to satisfy the property, Heap-Order.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?childeren.key\geq&space;parent.key\quad\quad&space;if\&space;the\&space;heap\&space;is\&space;min-heap" title="https://latex.codecogs.com/svg.image?childeren.key\geq parent.key\quad\quad if\ the\ heap\ is\ min-heap" /></center><br/>
&nbsp;&nbsp;If the heap is a max-heap, then the inequality sign is reversed. That is, we just make the binary tree whose root is the minimum or maximum and, the paths are in an increasing or decreasing order. And a heap has to be a complete binary tree. So, when the last node is inserted or updated, a heap has to satisfy the property of a complete binary tree. For that, the last node is the most right node of the lowest level. And, because of the property of complete binary trees, indices of nodes have the property below.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?for\&space;i=0...h-1,\&space;there\&space;are\&space;2^{i}\&space;nodes\&space;of\&space;depth\&space;i&space;" title="https://latex.codecogs.com/svg.image?for\ i=0...h-1,\ there\ are\ 2^{i}\ nodes\ of\ depth\ i " /></center><br/>
 &nbsp;&nbsp;As can be seen in the above minimum heap picture, the indexes of each node in the array are the same as when numbered from top to bottom, from left to right. If the heap stores n keys(nodes), there are at least one key at depth h, we have n &ge;1+2+…2<sup>h-1</sup> + 1. Thus, n>=2<sup>h</sup> and h<=logn.
 &nbsp;&nbsp;A heap can be implemented using an array. If parent node is stored in <i>A[i]</i>, the index of the left child is (2 * i) and the index of the right child is (2 * i + 1). We can compute indices with bit operations. When you compute left child, just shift the binary representation of <i>i</i> by one bit position. And when you compute right child, just shift the binary representation of <i>i</i> left by one bit position and add 1.



<br/><br/>
<p id = "2"><font size = "5"><b>2. How to keep Heap-Order with insertion and removal</b></font>
<hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;Before talking about how to build a heap, we have to know how to keep Heap-Order. (In this post, I will descript all heap, like min-heap.) There are two way called <b>‘Up-Heap’</b> and <b>‘Down-Heap’</b>. Up-Heap is used to insert node, and Down-Heap is used to remove node.<br/>
 &nbsp;&nbsp;When inserting a node at heap, follow the steps below.<br/>
 <center><img src = "https://user-images.githubusercontent.com/80208196/159768492-7fb829d5-d540-4d41-8c03-b33723c2b8ef.PNG" width="500" height="400"><br/>
<font size = "2">Insert</font></center>
 <ol>
    <li>Add the new node at the next last node position.</li>
    <li>Compare the key of the parent of the new node and the key of the new node.</li>
    <li>If the result of comparison contradicts with Heap-Order, swap the new node and its parent.</li>
    <li>Proceed step 2 and step 3 until the new node becomes the root or until Heap-Order is satisfied.
    </li>
</ol>
&nbsp;&nbsp;The steps except step 1 are called ‘Up-Heap’. ‘Up-Heap’ runs <b><i>O(h)</i></b> time, because the comparison operation and swapping operation proceeds only one time in each level. Moreover, ‘Up-Heap’ runs in <b><i>O(logn)</i></b> time because the height of a heap is O(logn).<br/>
&nbsp;&nbsp;In contrast, when removing minimum node, follow the steps below.<br/>
 <center><img src = "https://user-images.githubusercontent.com/80208196/159768501-486fb117-8012-4c1d-8ac0-995e0925d324.PNG" width="500" height="400"><br/>
<font size = "2">Remove Min</font></center>
<ol>
    <li>Return the key of the root.</li>
    <li>Assign the key of the last node to the root.</li>
    <li>Compare the key of the children of the root and the key of root.</li>
    <li>If the result of comparison contradicts with Heap-Order, swap the root and one of its child whose value is minimum(or maximum) among the root and the children of root. If the children have same value and the value is less than the value of root, whether root is swapped with left child or right one is no matter. Just keep swapping same direction of child.</li>
    <li>Proceed step 2 and step 3 until the root node becomes the leaf or until Heap-Order is satisfied.</li>
</ol>
&nbsp;&nbsp;The steps except step 1, 2 are called ‘Down-Heap’. ‘Down-Heap’ runs in <i><b>O(logn)</b></i> time, too.

<br/><br/>
<p id = "3"><font size = "5"><b>3. Build Heap</b></font>
<hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;We can build a heap with an unsorted array in O(nlogn) time. The unsorted array has n elements and we just insert all elements at the heap. But it is not efficient.<br/>
&nbsp;&nbsp;We know that the internal nodes of heaps are the root of subtrees of a heap. So, we just need to proceed Down-Heap for each internal node. Because Down-Heap runs in O(h) time, we just compute how many nodes there are in each level. By the property of a complete binary tree, the number of leaf nodes of the heap made by n elements are about n/2. So, the number of operation we need is<br/>
<center><img src="https://latex.codecogs.com/svg.image?\begin{align*}1\cdot&space;\frac{n}{4}&plus;2\cdot&space;\frac{n}{8}&plus;...&plus;(h\cdot&space;1)&space;&=&space;\sum_{k=1}^{h}\frac{k}{2^{k-1}}\\&space;&<&space;\frac{n}{4}\sum_{k=1}^{\infty}\frac{k}{2^{k-1}}&space;<&space;\frac{n}{4}\sum_{k=1}^{\infty}kx^{k-1}\\&space;&=&space;\frac{n}{4}\frac{d}{dx}\left&space;[&space;\sum_{k=0}^{\infty}x^{k}&space;\right&space;]=\frac{n}{4}\frac{d}{dx}\left[&space;\frac{1}{1-x}&space;\right&space;]\\&space;&=&space;\frac{n}{4}\frac{1}{(1-x)^{2}}=\frac{n}{4}\frac{1}{(1-1/2)^{2}}=n\end{align*}" title="https://latex.codecogs.com/svg.image?\begin{align*}1\cdot \frac{n}{4}+2\cdot \frac{n}{8}+...+(h\cdot 1) &= \sum_{k=1}^{h}\frac{k}{2^{k-1}}\\ &< \frac{n}{4}\sum_{k=1}^{\infty}\frac{k}{2^{k-1}} < \frac{n}{4}\sum_{k=1}^{\infty}kx^{k-1}\\ &= \frac{n}{4}\frac{d}{dx}\left [ \sum_{k=0}^{\infty}x^{k} \right ]=\frac{n}{4}\frac{d}{dx}\left[ \frac{1}{1-x} \right ]\\ &= \frac{n}{4}\frac{1}{(1-x)^{2}}=\frac{n}{4}\frac{1}{(1-1/2)^{2}}=n\end{align*}" /></center><br/>
&nbsp;&nbsp;So, the time complexity is <i><b>O(n)</b></i>.


<br/><br/>
<p id = "4"><font size = "5"><b>4. Heap Sort</b></font><hr style="border: solid 0.1px black;"></p>
<font size = "4"><b>How to draw the recursion tree</b></font>
&nbsp;&nbsp;Sorting n elements is easy to understand. Just build a heap with n elements and remove minimum until no elements are left in the heap. It needs O(logn) time for each element. So, It needs <i><b>O(nlogn)</b></i> time.