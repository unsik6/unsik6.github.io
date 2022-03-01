---
layout: post
title: "[CLRS Review] Chapter 4. Divide-and-Conquer"
date: 2022-02-04 01:30:00 +0900
category: CLRS_Review
---

<center>
        <table border ="1" width = "400">
            <tr>
                <td>
                <a href = "#1"><font size = "2">&nbsp;&nbsp;1. Divde-and-Conquer</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#2"><font size = "2">&nbsp;&nbsp;2. Recurrences</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#3"><font size = "2">&nbsp;&nbsp;3. The substitution method for solving recurrences</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#4"><font size = "2">&nbsp;&nbsp;4. The recursion-tree method for solving recurrences</font></a>
                </td>
            </tr>
            <tr>
                <td>
                <a href = "#5"><font size = "2">&nbsp;&nbsp;5. Solve the recurrence using the master method</font></a>
                </td>
            </tr>
        </table>
</center>
<br/><br/>

<p id = "1"><font size = "5"><b>1. Divde-and-Conquer</b></font></p>
<hr style="border: solid 0.1px black;">
&nbsp;&nbsp;Divide-and-Conquer is the algorithm solving the problem by dividing the original problem to smaller subproblems. Recalling Divide-and-Conquer, we solve the problem recursively by applying three steps at each level of the recursion.<br/>
&nbsp;&nbsp;At first, <b>Divide</b> the problem into a number of subproblems smaller than the original problem. There are two problem cases, one is called a <I><b>recursive case</b></I> where the problem is large enough to solve recursively. Another case is called a <I><b>base case</b></I> and it occurs when the problem is too small to solve recursively. The subproblem size does not always equal each other. When n/b is not an integer, we need floor and ceiling function to make n/b an integer. Therefore, each subproblem size does not equal each other.<br/>
&nbsp;&nbsp;Secondly, <b>Conquer</b> the subproblems by solving them recursively. If the subproblem size is small enough, we can solve it in a straightforward manner. In this case, It is Θ(1) time.
&nbsp;&nbsp;Finally, <b>Combine</b> the solutions to the subproblems into the solution for the original problem.


<br/><br/>
<p id = "2"><font size = "5"><b>2. Recurrences</b></font>
<hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;A recurrence is an equation or inequality that describes a function in terms of its value on smaller inputs.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?T(n)=\left\{\begin{matrix}\Theta&space;(1)\quad\quad\quad\quad\quad\quad&space;if\&space;n&space;=&space;1,\\2T(n/2)&plus;\Theta&space;(n)\quad\quad&space;if\&space;n&space;>&space;1\end{matrix}\right." title="T(n)=\left\{\begin{matrix}\Theta (1)\quad\quad\quad\quad\quad\quad if\ n = 1,\\2T(n/2)+\Theta (n)\quad\quad if\ n > 1\end{matrix}\right." /></center>
<br/>A recursive algorithm might divide subproblems into unequal sizes. And, subproblems are not necessarily constrained to be a constant fraction of the original problem size. There are lots of forms of recurrences. We normally state recurrences without boundary conditions, <i>T(1)</i>, because <i>T(n)</i> is <i>Θ(1)</i> if n is small enough.
<br/><br/>
&nbsp;&nbsp;The methods for solving recurrence provide asymptotic “Θ” or “O” bounds on the solution.<br/>
<ol>
    <li><i><b>Substitution method</b></i>: We guess a bound and then use mathematical induction to prove that is correct.</li>
    <li><i><b>Recursion-tree method</b></i>: The tree that was converted from the recurrence has nodes that represent the costs incurred at various levels of the recursion. To solve the recurrences, use the techniques for bounding summations.</li>
    <li><i><b>Master method</b></i>:<br/><br/>
    <center><img src="https://latex.codecogs.com/svg.image?T(n)=aT(n/b)&plus;f(n)\quad&space;where\&space;a\geq&space;1,\&space;b>&space;1\&space;and\&space;f(n)\&space;is\&space;given\&space;function" title="T(n)=aT(n/b)+f(n)\quad where\ a\geq 1,\ b> 1\ and\ f(n)\ is\ given\ function" /></center><br/>
    &nbsp;&nbsp;<i>a</i> is the number of subproblems in the term that input is <i>n</i>. <i>n/b</i> is the subproblem size. And we need <i>f(n)</i> time to divide the problem and combine the solutions to the subproblems of which size is <i>n/b</i> into the solution for the problem of which size is <i>n</i>.<br/>
    &nbsp;&nbsp;It also works in form of inequality to determining upper and lower bounds.<br/><br/>
    <center><img src="https://latex.codecogs.com/svg.image?T(n)\leq&space;aT(n/b)&plus;f(n)\quad&space;for\&space;O-notation&space;" title="T(n)\leq aT(n/b)+f(n)\quad for\ O-notation " /></center>
    <center><img src="https://latex.codecogs.com/svg.image?T(n)\geq&space;&space;&space;aT(n/b)&plus;f(n)\quad&space;for\&space;\Omega&space;-notation&space;" title="T(n)\geq aT(n/b)+f(n)\quad for\ \Omega -notation " /></center><br/>
    </li>
    <li>
    &nbsp;&nbsp;(not method) To prove loose upper and lower bounds on the recurrence and then reduce the range of uncertainty.
    </li>
</ol>

<br/><br/>
<p id = "3"><font size = "5"><b>3. The substitution method for solving recurrences</b></font>
<hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;The substitution method for solving recurrences are comprised with two steps:<br/>
<ol>
    <li>Guess the form of the solution.</li>
    <li>Use mathematical induction to find the constants and show that the solution works.</li>
</ol>
&nbsp;&nbsp;At first, we have to guess the appropriate form of the solution, and substitute recurrences to the form.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?To\&space;prove\&space;''\Theta&space;'',\&space;T(n)=cf(n)\quad&space;f(n)\&space;is\&space;the\&space;form\&space;of\&space;solution\&space;guessed," title="To\ prove\ ''\Theta '',\ T(n)=cf(n)\quad f(n)\ is\ the\ form\ of\ solution\ guessed," />
<img src="https://latex.codecogs.com/svg.image?To\&space;prove\&space;''O&space;'',\&space;T(n)\leq&space;cf(n)\quad&space;f(n)\&space;is\&space;the\&space;form\&space;of\&space;solution\&space;guessed," title="To\ prove\ ''O '',\ T(n)\leq cf(n)\quad f(n)\ is\ the\ form\ of\ solution\ guessed," />
<img src="https://latex.codecogs.com/svg.image?To\&space;prove\&space;''\Omega&space;&space;'',\&space;T(n)\geq&space;&space;cf(n)\quad&space;f(n)\&space;is\&space;the\&space;form\&space;of\&space;solution\&space;guessed," title="To\ prove\ ''\Omega '',\ T(n)\geq cf(n)\quad f(n)\ is\ the\ form\ of\ solution\ guessed," />
</center><br/>
&nbsp;&nbsp;The substitution method requires us to prove that the equation or inequality for an appropriate choice of the constant <i>c&#62;0</i>. For that, start by assuming that the formulas holds for all positive <i>m&#60;n</i>, in particular for <i>m = n/b</i>. &#40;<i>n/b</i> is the subproblem size.&#41; After that, use mathematical induction to find the constants and show that the solution works. But we have to prove that our solution holds for the boundary conditions, to use mathematical induction. Typically, it is to prove that the boundary conditions are suitable as base cases for the inductive proof.<br/>
&nbsp;&nbsp;However, sometimes it doesn’t work when n is too small. We can solve this easily. Just prove that our solution holds for <i>n≥n<sub>0</sub></i> where a constant that we get to choose. It means removing <i>T(i)</i> where <i>i&#60;n<sub>0</sub></i> from consideration in the inductive proof, and replace T(n<sub>0</sub>) as base cases. In this case, the base case of recurrences and the base cases of the inductive proof is distinct.<br/>
&nbsp;&nbsp;For solving recurrences using the substitution method, we have to make a good guess. There are three heuristics to do that.
<ol>
    <li>
    You can solve the recurrences that is similar to one you have seen before.
    </li>
    <li>
    Prove upper and lower bounds on the recurrence and then reduce the range of uncertainty to obtain more tight bounds.
    </li>
    <li>
    Use recursion trees.
    </li>
</ol>
&nbsp;&nbsp;When you guess an asymptotic bound on the solution of a recurrence and prove it in inductive proof, follow the tips below because the proof is not easy.<br/>
<ol>
    <li>
    It is not easy to prove the detailed bound by inductive assumption. If you correctly guess an asymptotic bound on the solution of a recurrence, sometimes it is impossible to prove your bound in inductive proof. So, <b>just subtract a lower-order term.</b>
    </li>
    <li>
    But that isn’t mean you don’t need to <b>prove recurrences explicitly.</b> You have to prove T(n)≤cn in the example below.<br/><br/>
    <center><img src="https://latex.codecogs.com/svg.image?\begin{align*}&space;T(n)&space;&\leq&space;2(c\left&space;\lfloor&space;n/2\right&space;\rfloor)&plus;n&space;\\&space;&\leq&space;cn&space;&plus;&space;n&space;\\&space;&=&space;O(n)\&space;\rightarrow&space;wrong\end{align*}" title="\begin{align*} T(n) &\leq 2(c\left \lfloor n/2\right \rfloor)+n \\ &\leq cn + n \\ &= O(n)\ \rightarrow wrong\end{align*}" /></center>
    </li>
    <li>
    <b>Change the variables or anything that is too complicated or difficult to use for proof.</b> Just make the formula simple.
    </li>
</ol>
<br/><br/>
<p id = "4"><font size = "5"><b>4. The recursion-tree method for solving recurrences</b></font><hr style="border: solid 0.1px black;"></p>
<font size = "4"><b>How to draw the recursion tree</b></font>
&nbsp;&nbsp;In Recursion tree, each node represents the cost of a subproblem. We obtain the total cost of recurrences, as summing all elements of the set of the cost per level. The good guess devised using the recursion tree can be proved by the substitution method.<br/><br/>
<center><img src = "https://user-images.githubusercontent.com/80208196/156223232-cce2f1a8-f232-45cd-92d3-17a14fa8bb63.png" width="300" height="150"><img src = "https://user-images.githubusercontent.com/80208196/156223238-dffe55fa-c264-4609-80d4-fc1f2b1257c5.png" width="600" height="350"><br/>
<img src="https://latex.codecogs.com/svg.image?T(n)=2T(\left&space;\lfloor&space;n/3\right&space;\rfloor)&plus;\Theta&space;(n^2)" title="T(n)=2T(\left \lfloor n/3\right \rfloor)+\Theta (n^2)" /></center><br/>
&nbsp;&nbsp;Draw a root node, <i>T(n)</i>. Then expand the tree by drawing the children of the root node. The number of the children are equal to the number of subproblems. After that, exchange the value of root node to the cost that is spent to divide the problem or the subproblems and to combine the subproblems. Next, you give the children the recurrence of subproblems, like <i>T(n/2)</i>.<br/>
&nbsp;&nbsp;After that, you keep on expanding the tree by drawing the children of each node until they meet base case, <i>T(1)</i>. As a consequence, the internal nodes(it is recursive case) represent the cost that was spent to divide the problem or the subproblems and to combine the subproblems.<br/><br/>
<font size = "4"><b>Solve the recurrence using the recursion tree</b></font>
&nbsp;&nbsp;We can solve the recurrence by computing all cost of the recursion tree. Before summing all cost of the recursion tree, we need to sum the cost of each level. And before that, we need to compute how many levels are in the tree. We can derive an equation about the level and the subproblem sizes. In the picture above, the subproblem size in level i is n/3^i. Thus, we can derive the level of base case from<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?1=n/3^i\&space;\rightarrow&space;\&space;i=\log_3&space;n" title="1=n/3^i\ \rightarrow \ i=\log_3 n" /></center><br/>
&nbsp;&nbsp;So, the recursion tree has log_3⁡n+1 levels. (the depth of root is 0). Now then, compute the sum of the costs of each level. In the picture above, there are two subproblems, and the cost of each node is <img src="https://latex.codecogs.com/svg.image?c(n/3^i)^2\&space;(i=level)" title="c(n/3^i)^2\quad (i=level)" /> So, the sum of the cost in each level <i>i</i> is <img src="https://latex.codecogs.com/svg.image?2^ic(n/3^i)^2=c(2/9)^in^2\&space;(i=level)" title="2^ic(n/3^i)^2=c(2/9)^in^2\ (i=level)" /> In the base level, the sum is <img src="https://latex.codecogs.com/svg.image?\Theta(1)*2^{log_3&space;2}=\Theta&space;(n^{log_3&space;2})" title="\Theta(1)*2^{log_3 2}=\Theta (n^{log_3 2})" />. Thus, if we sum the costs of each level by summing <img src="https://latex.codecogs.com/svg.image?c(2/9)^in^2\&space;(i=level,\&space;where\&space;0\leq&space;i\leq&space;log_3&space;n-1)" title="c(2/9)^in^2\ (i=level,\ where\ 0\leq i\leq log_3 n-1)" /> and <img src="https://latex.codecogs.com/svg.image?\Theta(n^{log_3&space;2})&space;" title="\Theta(n^{log_3 2}) " />.<br/><br/>
<img src="https://latex.codecogs.com/svg.image?\begin{align*}T(n)&space;&=&space;cn^2&plus;(2/9)cn^2&plus;(2/9)^2cn^2&plus;\cdots&space;&plus;(2/9)^{log_3&space;n-1}&plus;\Theta&space;(n^{log_3&space;2})\\&space;&=&space;\sum_{i=0}^{log_3&space;n-1}(2/9)^icn^2&plus;\Theta&space;(n^{log_3&space;2})\\&space;&=&space;\frac{(2/9)^{log_3&space;n}-1}{(2/9)-1}cn^2&plus;\Theta&space;(n^{log_3&space;2})\end{align*}" title="\begin{align*}T(n) &= cn^2+(2/9)cn^2+(2/9)^2cn^2+\cdots +(2/9)^{log_3 n-1}+\Theta (n^{log_3 2})\\ &= \sum_{i=0}^{log_3 n-1}(2/9)^icn^2+\Theta (n^{log_3 2})\\ &= \frac{(2/9)^{log_3 n}-1}{(2/9)-1}cn^2+\Theta (n^{log_3 2})\end{align*}" /><br/><br/>
&nbsp;&nbsp;We can derive the lower bound from the formula above.<br/><br/>
<img src="https://latex.codecogs.com/svg.image?\begin{align*}T(n)&=\sum_{i=0}^{log_3&space;n-1}(2/9)^icn^2&plus;\Theta&space;(n^{log_3&space;2})\\&<&space;\sum_{i=0}^{\infty}(2/9)^icn^2&plus;\Theta&space;(n^{log_3&space;2})\\&=\frac{1}{(1-2/9)}cn^2&plus;\Theta&space;(n^{log_3&space;2})=O(n^2)\end{align*}" title="\begin{align*}T(n)&=\sum_{i=0}^{log_3 n-1}(2/9)^icn^2+\Theta (n^{log_3 2})\\&< \sum_{i=0}^{\infty}(2/9)^icn^2+\Theta (n^{log_3 2})\\&=\frac{1}{(1-2/9)}cn^2+\Theta (n^{log_3 2})=O(n^2)\end{align*}" /><br/><br/>
&nbsp;&nbsp;So, we have derived a guess of <img src="https://latex.codecogs.com/svg.image?T(n)=O(n^2)" title="T(n)=O(n^2)" /> for original recurrence <img src="https://latex.codecogs.com/svg.image?T(n)=2T(\left&space;\lfloor&space;n/3\right&space;\rfloor)&plus;\Theta&space;(n^2)" title="T(n)=2T(\left \lfloor n/3\right \rfloor)+\Theta (n^2)" />. After deriving the guess, we have to verify the guess is correct using the substitution method. In our example, we have to verify <img src="https://latex.codecogs.com/svg.image?T(n)\leq&space;dn^2" title="T(n)\leq dn^2" /> for some constant <img src="https://latex.codecogs.com/svg.image?d>0" title="d>0" /> using the constant <img src="https://latex.codecogs.com/svg.image?c>0" title="c>0" />.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?\begin{align*}&space;T(n)&\leq&space;2T(\left&space;\lfloor&space;n/3\right&space;\rfloor)&plus;cn^2&space;\\&space;&\leq&space;2d(n/3)^2&plus;cn^2&space;\\&space;&=&space;(2/9)dn^2&plus;cn^2\leq&space;dn^2\&space;(d\geq&space;(9/7)c)\end{align*}" title="\begin{align*} T(n)&\leq 2T(\left \lfloor n/3\right \rfloor)+cn^2 \\ &\leq 2d(n/3)^2+cn^2 \\ &= (2/9)dn^2+cn^2\leq dn^2\ (d\geq (9/7)c)\end{align*}" /><br/>
<font size = "2">The recursion-tree method is not limited to when the subproblem size is the same.</font></center>

<br/><br/>
<p id = "5"><font size = "5"><b>5. Solve the recurrence using the master method</b></font><hr style="border: solid 0.1px black;"></p>
&nbsp;&nbsp;Using the master method is the simplest way to solve the recurrence. Just check that the recurrence (which is the form below) satisfies the terms of the master method. If it is, just apply the master method to the recurrence.<br/><br/>
<center><img src="https://latex.codecogs.com/svg.image?T(n)=aT(n/b)&plus;f(n)\quad&space;where\&space;a\geq&space;1,\&space;b>1\&space;and\&space;f(n)\&space;is\&space;given\&space;function" title="T(n)=aT(n/b)&plus;f(n)\quad&space;where\&space;a\geq&space;1,\&space;b>1\&space;and\&space;f(n)\&space;is\&space;given\&space;function" /></center><br/><br/>
&nbsp;&nbsp;<i>n/b</i> b is not always an integer. However, in the asymptotic behavior of the recurrence, there is no matter replacing <img src="https://latex.codecogs.com/svg.image?T(\left&space;\lfloor&space;n/b\right&space;\rfloor)" title="T(\left \lfloor n/b\right \rfloor)" />, <img src="https://latex.codecogs.com/svg.image?T(\left&space;\lceil&space;n/b\right&space;\rceil)" title="T(\left \lceil n/b\right \rceil)" /> with <img src="https://latex.codecogs.com/svg.image?T(n/b)" title="T(n/b)" />. We can solve the recurrence in 3 terms.<br/><br/>
<img src="https://latex.codecogs.com/svg.image?if\&space;f(n)=O(n^{log_b&space;a-\epsilon&space;})\&space;for\&space;some\&space;constant\&space;\epsilon&space;>0,\&space;then\&space;T(n)=\Theta&space;(n^{log_b&space;a})" title="if\ f(n)=O(n^{log_b a-\epsilon })\ for\ some\ constant\ \epsilon >0,\ then\ T(n)=\Theta (n^{log_b a})" /><br/><br/>
<img src="https://latex.codecogs.com/svg.image?if\&space;f(n)=\Theta&space;(n^{log_b&space;a}),\&space;then\&space;T(n)=\Theta&space;(n^{log_b&space;a}logn)" title="if\ f(n)=\Theta (n^{log_b a}),\ then\ T(n)=\Theta (n^{log_b a}logn)" /><br/><br/>
<img src="https://latex.codecogs.com/svg.image?\\&space;if\&space;f(n)=\Omega&space;(n^{log_b&space;a&plus;\epsilon&space;})\&space;for\&space;some\&space;constant\&space;\epsilon&space;>0\\&space;and\&space;if\&space;af(n/b)\leq&space;cf(n)\&space;for\&space;some\&space;constant\&space;c<1\&space;and\&space;all\&space;sufficiently\&space;large\&space;n,\\then\&space;T(n)=\Theta&space;(f(n))" title="\\ if\ f(n)=\Omega (n^{log_b a+\epsilon })\ for\ some\ constant\ \epsilon >0\\ and\ if\ af(n/b)\leq cf(n)\ for\ some\ constant\ c<1\ and\ all\ sufficiently\ large\ n,\\then\ T(n)=\Theta (f(n))" /><br/><br/>
&nbsp;&nbsp;We can find that <i>f(n)</i> and <img src="https://latex.codecogs.com/svg.image?n^{log_b&space;a}" title="n^{log_b a}" />  affects the solution of the recurrence. In all case, the larger is the solution of the recurrence. But the simple comparison between <i> f(n)</i> and <img src="https://latex.codecogs.com/svg.image?n^{log_b&space;a}" title="n^{log_b a}" /> is not only condition of the master method. The comparison must satisfy polynomially. Therefore, as there are gaps among cases, you have to check if the recurrence you want to solve satisfies any case.