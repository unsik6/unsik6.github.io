---
layout: post
title: NLP-Word Embedding 1) One-Hot Encoding
subtitle: Sparse Representation
categories: NLP
tags: [AI, NLP, Word Embedding, Preprocessing]
---
## 1. Word Embedding
<hr>
&nbsp;&nbsp;Because language that consist of words, prepositionas and etc can not be computed, it have to be converted to some computable representation. So, in data processing stage, input texts is converted to  a vector, and it is called <i><b>'Word Embedding'</b></i>. There are a lot of word embedding methods. In this post, <b><i>'One-Hot Encoding'</i></b> will be introduced.

<br/><br/>

## 2. One-Hot Encdoing
<hr>
&nbsp;&nbsp;There are two kinds of data, <u>Categorical Value</u> and <u>Continuous Value</u>. Contrary to continuous value such as temperature and height, categorical value is discrete value such as class and word. Generally, we convert categorical value some computable value such as integer. But its cardinal numbers is not numberic value that has size or rank. For example, if two temperatures(continuous value) are similar, it means that the kinetic energy of the molecule is similar. And if a temperature is higher than others, it is hotter.<br/><br/>

|Index|0|1|2|3|...|1,000,000|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Class|Cats|Ships|Papers|Knifes|...|Dogs|

<center><span style = "opacity:0.5">fig 1. a mapping table of some image classes</span></center><br/>
&nbsp;&nbsp;Whereas, in classification task, the indices of image classes labeled cats, ships and etc are not mapped by similarity. If cats class is indexed to 0, it works well whether dogs class is indexed to 1 or 1,000,000. Moreover, The distance of classes can not be used. In fig 1, although cats are more similar with dogs than ships, the distance of Cats class and Ships class is 1, less than the distance of Cats class and Dogs class, 1,000,000.<br/><br/>

| |Index|Cats|Ships|Papers|...|Dogs|
|:---:|:---:|:---:|:---:|:---:|:---:|
|Cats|0|1|0|0|...|0|
|Ships|1|0|1|0|...|0|
|Papers|2|0|0|1|...|0|
|Knifes|3|0|0|0|...|0|
|...|...|...|...|...|...|...|
|Dogs|1,000,000|0|0|0|...|1|

<center><span style = "opacity:0.5">fig 2. One-Hot vectors by One-Hot Encoding</span></center><br/>

&nbsp;&nbsp;One-Hot encoding is a vector representation, whose dimensions is mapped to objects(words or classes). Objects are converted to <i><b>One-Hot vector</b></i>.  One-Hot vector of an object is allocated 1 at the dimension mapped to the object, and all other dimensional value is 0. For example, in fig 2, the index of Papers class is 2. It means the second dimension of all One-Hot vectors are mapped to Papers class. So, One-Hot vector of Papers class is (0, 0, 1, 0, ...). <u><b>One-Hot vector is sparse vector because almost elements of One-Hot vector is 0. (One-Hot Encoding is sparse representation)</b></u> And cosine similarity between all One-Hot vectors is 0, because two One-Hot vectors are orthogonal.<br/>
&nbsp;&nbsp;In NLP, the words or tokens are converted One-Hot vectors.

<br/><br/>

## 3. Drawbacks of One-Hot Encoding
<hr/>

1. Computing the distance between vectors is hard. However, there is similarity(distance) between some words of languages. For example, cats are more similar with dogs than ships semantically.
2. We need very large memory space to implement One-Hot vectors. If there are a dictionary whose size is <i>N</i>, we need <i>O(N<sup>2</sup>)</i> space.

<br/>
&nbsp;&nbsp;So, One-Hot Encoding is not prefered. There are a lot of embedding method including dense representation(truely word embedding).

<br/><br/>

## Refers
<hr>
<a href = "https://wikidocs.net/book/2155"><i>딥 러닝을 이용한 자연어 처리 위키독스</i> </a><br/>