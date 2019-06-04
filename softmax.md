## Softmax

1. Softmax is a straightforward extension of logistic regression for multi-class classification. Softmax activation takes a whole vector as input and outputs a vector of the same size. This is in contrast to ReLU or sigmoid which work on a single real number.(When applied to vectors, they do it element-wise i.e on single random numbers. In contrast, softmax uses the entire vector)

2. $g(z)=\frac{\large{e^{z}}}{\sum_{i=1}^{C}{e^{\large{z_i}}}}$ 

3. When C=2, one can see that it is equivalent to logistic regression best explained by [this](https://stackoverflow.com/a/43174772) StackOverflow answer.

4. The cost function that is used here if softmax is the last layer(which it usually is, because that's the whole point) is:

   $\sum_{i=1}^{C}{-y^{(i)}\log{(\hat{y}^{(i)}})}$

5. However, my personal opinion is, it should be:

   $\sum_{i=1}^{C}{-y^{(i)}\log{(\hat{y}^{(i)})}-(1-y^{(i)})\log{(1-\hat{y}^{(i)}})}$

6. This is because the first one penalizes non-adherance to $y^{(i)}$ only if $y^{(i)}$ is $1$ ! If $y^{(i)}$ is $0$, then no matter how bad $\hat{y}^{(i)}$, there's no penalty. This won't give a very good model. If we penalize this too, as done in my second cost function, then we will get sharper results I think.

7. Proof for derivative expression:
   $$
   \hat{y}=\frac{e^{z}}{\sum_{j=1}^{C}z_j} \\
   L(\hat{y},y)=-\sum_{j=1}^{C}y_j\log{(\hat{y_j})} \\
   \begin{align*}
   \frac{\partial L}{\partial z_i}&=-\frac{y_i}{\hat{y_i}}\frac{\partial \hat{y_i}}{\partial z_i} - \sum_{j \neq i}\frac{y_j}{\hat{y_j}}\frac{\partial \hat{y_j}}{\partial z_i} \\
   &= ... \\
   &= \hat{y_i}\sum_{j=1}^{C}y_j - y_i \\
   &= \hat{y_i} - y_i
   \end{align*}
   $$

