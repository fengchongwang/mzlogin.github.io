---
layout: post
title: "Andrew Ng's Deep Learning Course notes"
author: "Fengchong Wang"
---
# Going Through Coursera Deep Learning Course
## First course
### A good example to explain relu and NN
<figure class="image"><img src="/images/blog/nn_explanation.png" alt="{{}}"><figcaption>Each neuron in the figure can be regarded as a relu computation on the weighted sum of the inputs</figcaption></figure>

### Why relu instead of sigmoid?
ReLU does not have small gradient area as sigmoid &rarr; training speed much higher.

### Notation guide
$m$ - number of samples

$\mathbf{x}\in \mathbb{R}^{n_x\times 1}$, is a $n_x$ dimensional column vector,

$\mathbf{X}=[\mathbf{x}^{(1)}, \mathbf{x}^{(2)}, ..., \mathbf{x}^{(m)}]$, is a $n_x\times m$ matrix,

$y\in \{0, 1\}$,

$\mathbf{Y} = [y^{(1)},y^{(2)},...,y^{(m)}]\in \mathbb{R}^{1\times m}$, is a $m$ dimensional row vector.

### Logistic regression
**Task:** predict $\hat{y}=P(y=1\|\mathbf{x})$.

**Model:** assume $y=\sigma (\mathbf{w}^T\mathbf{x}+b)$ where $\mathbf{w}\in \mathbb{R}^{n_x\times 1}$ and $b\in \mathbb{R}$.

**Intuition:** given ${(\mathbf{x}^{(1)}, y^{(1)}),(\mathbf{x}^{(2)}, y^{(2)}),...,(\mathbf{x}^{(m)}, y^{(m)})}$, want every $\hat{y}^{(i)}\approx y^{(i)}$. To do this, define loss function of an estimated $\hat{y}$ to be $\mathcal{L}=-[ylog\hat{y} + (1-y)log(1-\hat{y})]$.

**Cost function:**
$J(\mathbf{w},b)=-\frac{1}{m}\sum_{i=1}^{m}[ylog\hat{y} + (1-y)log(1-\hat{y})]$

**Task becomes:**

Find $\mathbf{w},b$ to minimize $J$.

**Solution:**
\begin{equation}
\frac{\partial J}{\partial \mathbf{w}}=-\frac{1}{m}\mathbf{X}(\mathbf{y}-\mathbf{\hat{y}})
\end{equation}

\begin{equation}
\frac{\partial J}{\partial b}=-\frac{1}{m} np.sum(\mathbf{y}-\mathbf{\hat{y}})
\end{equation}
