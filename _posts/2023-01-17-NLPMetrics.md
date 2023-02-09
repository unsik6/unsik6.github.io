---
layout: post
title: NLP) Metrics - Writing
subtitle: Outline of Metrics used in NLP
categories: NLP
tags: [AI, NLP, Metric]
---
&nbsp;&nbsp;This post is the outline of metrics used in NLP. So, there are only name, category, some relation with other metrics and short description. I will write post about each metric, and link them in this post.

## * Two Terms of Evaluation
<hr>

1. <b>Instrinsic Evaluation</b>: Evaluation by human. It is most perfect evaluation. Depending on who scores, there is a deviation in the scoring results, because there is no clear grading standard especially in NLP. Futhermore, it spends lots of time and cost.
2. <b>Extrinsic Evaluation</b>: Evaluation by a score metric such as BLEU or ROUGUE. This runs as program, so mass evaluation and automation are available, with cost and time advantages. But it is not guaranteed that the result of score metrics is not equal or similar with one of evaluation by human.

&nbsp;&nbsp;There are two aspects of evaluation. These are different about how the model is evaluated. I will introduce intrinsic evaluation used in NLP tasks.
> On the other aspect, the definition of two words is different. In aspect of <u>evaluation to models in an application</u>, intrinsic evaluation focuses on intermediary objectives related directly the performance of an NLP component on a defined subtask, and extrinsic evaluation focuses on the performance of the final objective of the component on the complete application. For example, a text summarization application consists of word embedding model and summarization model. Intrinsic evaluation is that each models in the application is evaluated separately. In another aspect, <u>whether comparision with other models is included or not is matter.</u> In intrinsic evaluation, the model is evaluated independently. Contrary to extrinsic evaluation is consist of performance comparsion with other models.

<br/><br/>

## [1] Confusion Matrix
<hr>
<img src = "https://user-images.githubusercontent.com/80208196/212989316-725128cd-4112-4365-83cd-b5be12340ca6.png">
<center><span style = "opacity:0.5"><a href = "https://medium.com/analytics-vidhya/what-is-a-confusion-matrix-d1c0f8feda5">ref. Anuganti Suresh, "What is a confusion matrix?"</a></span></center>

### 1. Accuracy
### 2. Precision
### 3. Recall
### 4. F1-Score
### 5. AUC

<br/><br/>

## [2] Statistics
<hr>

### 1. MRR
### 2. MAP
### 3. RMSE
### 4. MAPE

<br/><br/>

## [3] BLUE
<hr>

<br/><br/>

## [4] Alt to BLEU
<hr>

### 1. METEOR
### 2. PPL
### 3. STM
### 4. RIBES
### 5. MEWR

<br/><br/>

## [5] ROUGE
<hr>

### 1. ROUGE-N
### 2. ROUGE-L
### 3. ROUGE-W
### 4. ROUGE-S
### 5. ROUGE-SU

<br/><br/>

## [6] Alt to ROUGE
<hr>

### 1. ROUGE-WE
### 2. ParaEval
### 3. ROUGE 2.0

<br/><br/>

## [7] RDASS
<hr>

## Refers
<hr>

<a href = "https://velog.io/@crosstar1228/NLPRouge-score-Summarization%EC%9D%98-%ED%8F%89%EA%B0%80-Metric">crosstar1228, "[NLP]Rouge score - Summarization의 평가 Metric"</a><br/>
<a href = "https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9">Koo Ping Shung, "Accuracy, Precision, Recall or F1?"</a><br/>
<a href = "https://towardsdatascience.com/the-most-common-evaluation-metrics-in-nlp-ced6a763ac8b">Kurtis Pykes, "The Most Common Evaluation Metrics In NLP"</a><br/>
<a href = "https://en.wikipedia.org/wiki/Confusion_matrix">wikipedia, "Confusion Matrix"</a><br/>
<a href = "https://www.youtube.com/watch?v=vtYDyGGeQyo">Rahul Patwari Youtube, "The tradeoff between sensitivity and specificity"</a><br/>
<a href = "https://bioinformaticsandme.tistory.com/328">BioinformaticsAndMe, "AUC-ROC 커브"</a><br/>
<a href = "https://lamttic.github.io/2020/03/20/01.html">Iamttic, "정보 검색(Information Retrieval) 평가는 어떻게 하는 것이 좋을까?(2/2)"</a><br/>
<a href = "https://blog.naver.com/PostView.naver?blogId=owl6615&logNo=221537580561&redirect=Dlog&widgetTypeCall=true&directAccess=false">해솔, "회귀모형 평가하기 - RMSE(평균 제곱근 오차)"</a><br/>
<a href = "https://acdongpgm.tistory.com/102">Acdong, "[기계학습]모형의 성능 지표 ( MSE , MAPE , 정확도,정밀도,재현율,특이도 , F1 measure , ROC Curve)"</a><br/>
<a href = "https://wikidocs.net/book/2155">"딥 러닝을 이용한 자연어 처리 입문" 위키독스</a><br/>
<a href = "https://donghwa-kim.github.io/BLEU.html">Donghwa KIM, "BLEU Score"</a><br/>
<a href = "https://hulk89.github.io/neural%20machine%20translation/2017/06/05/BLEU/">hulk89, "BLEU의 모든 것"</a><br/>
<a href = "https://supkoon.tistory.com/18">supkoon, "[자연어처리[Metric] BLEU score : bilingual Evaluation Understudy"</a><br/>
<a href = "https://www.lengoo.com/blog/mt-for-beginners-what-is-bleu-and-what-is-wrong-with-it/">SINA BREITENBACH, "MT for Beginners: What is BLEU and what is wrong with it?"</a><br/>
<a href = "https://towardsdatascience.com/evaluating-text-output-in-nlp-bleu-at-your-own-risk-e8609665a213">Rachael Tatman, "Evaluating Text Output in NLP: BLEU at your own risk"</a><br/>
<a href = "https://machinelearninginterview.com/topics/machine-learning/meteor-for-machine-translation/">MLNerds, "METEOR metric for machine translation"</a><br/>
<a href = "https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=datajuny&logNo=221565052342">Juny, "sequence to sequence 모델의 평가방법"</a><br/>
<a href = "https://misconstructed.tistory.com/64">misconstructed, "[논문 리뷰] How NOT To Evaluate Your Dialogue System: An Empirical Study of Unsupervised Evaluation Metrics for Dialogue Response Generation (ENMNLP 2016)"</a><br/>
<a href = "https://towardsdatascience.com/perplexity-in-language-models-87a196019a94">Chiara Campagnola, "Perplexity in Language Models"</a><br/>
<a href = "https://bo-son.github.io/2019/05/19/nlg_metrics/">bo-son, "Automatic Evaluation Metrics for NLG"</a><br/>
<a href = "https://pypi.org/project/subtree-metric/">pypi, "Subtree Metric Package"</a><br/>
<a href = "https://huffon.github.io/2019/12/07/rouge/">devfon, "예시를 통한 ROUGE 성능 지표의 이해"</a><br/>
<a href = "https://pdfs.semanticscholar.org/60b0/5f32c32519a809f21642ef1eb3eaf3848008.pdf">Chin-Yew Lin, "ROUGE: A Package for Automatic Evaluation of Summaries"</a><br/>
<a href = "https://kakaoenterprise.github.io/deepdive/210729#edc6:fn-back:1">Kakao Enterprise AI Research, "텍스트 요약 모델 성능 평가를 위한 새로운 척도, RDASS를 소개합니다."</a><br/>
<a href = "https://www.researchgate.net/figure/Difference-between-extrinsic-and-intrinsic-evaluation-for-semantic-grounding-in-language_fig1_362089773">Probing Semantic Grounding in Language Models of Code with Representational Similarity Analysis - Scientific Figure on ResearchGate</a><br/>
<a href = ""></a><br/>
