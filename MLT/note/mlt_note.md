<link href="./style/markdown.css" ref="stylesheet"></link>

# Algorithmic Game Theory and Applications

## Content
<!-- TOC -->

- [Algorithmic Game Theory and Applications](#algorithmic-game-theory-and-applications)
  - [Content](#content)
  - [Lecture1 Introduction](#lecture1-introduction)
  - [Lecture2 PAC Learning](#lecture2-pac-learning)

<!-- /TOC -->
## Lecture1 Introduction
1. Machine Learning Types
   1. Classification
   2. Clustering
   3. Regression

2. Observations of learning
   1. Objective of learning is to find a simpler representation of data
   2. We cannot know the actual distribution of data
   3. The algorithm searches over a class set of models and outputs the optimal one
      1. Neural networks
      2. Support vector machines 
      3. Decision trees

3. For a known class of models, we can represent them by a vector of numbers. The vector of numbers does not indicate the type of model, but its size is the size of the model. 
   1. Neural networks: A vector of edge weights
   2. SVM: A vector of points
   3. Regression: Coefficients of polynomials

4. Notations
   1. Domain set  <span style="color: red">&chi;</span>: From which data is sampled
   2. Label set <span style="color: red">y</span> : From which labels are drawn 
   3. Training data <span style="color: red">S</span> = {$(x_{1},\ y_{1}),\ ...\ ,\ (x_{m},\ y_{m})$}
   4. Model, hypothesis, classifier, predictor <span style="color: red">h</span>: A function h: &chi; &rightarrow; y. h(x) returns a predicted label y. 
   5. Hypothesis or model class <span style="color: red">&Eta;</span> : The set of functionsfrom which h is chosen
   6. Algorithm <span style="color: red">A</span> : Chooses hypothesis h based on S
   7. Data generating distribution <span style="color: red">D</span> : An unknown probability distribution over &chi;. The training data is assumed to be sampled from D.
      1. We also assum there is a function f giving true labels of data
      2. Both D and f are unknown to us. 
   8.  Loss/Error function <span style="color: red">L</span>: the probability that label predicted by h will not match the true label

5. Empirical risk minimization (ERM): 跟真实标签不一样的个数 &div; 样本个数。 Find h with minimum $L_{S}(h)$

6. Observations of ERM: 
   1. It is difficult to find the minimum loss $L_{min}$ because:
      1. We do not know the minimum loss is
      2. not easy to search in an infinite model class
   2. We can ensure loss is approximately minimum, that is $L_{h} \leq (1\ +\ \epsilon)L_{min}$
   3. We work on a random sample of D, so the model is still probalistic and we can just approximate. 

7. Probably Approximately Correct learning (PAC learning): $Pr[(L_{h}\ -\ L_{min})\ \leq \epsilon] \geq 1\ -\ \delta$

8. Sample complexity: finite hypothesis classes need
   $$
      m_{H}(\epsilon,\delta)\ \leq \lceil \frac{\log(|\Eta|/\delta)}{\epsilon} \rceil
   $$

7. VC dimension: a measure of complexity of the class of hypotheses or models (a finite number used to represent the potential of the class). For finite classes, we use VCdim(&Eta;) instead of |&Eta;|

8. Bias and complexity tradeoff: when choose a hypothesis class, we risk
   1. take a restricted or simpler class, means models are biased towards those types of hypothesis
   2. The class has high complexity, rrisk overfitting

9. No-Free-Lunch theorem: Every algorithm fails somewhere. So we need a hypothesis class and set some parameters, such as degree of polynomial, number of neurons...

10. Privacy (see lec notes)

## Lecture2 PAC Learning