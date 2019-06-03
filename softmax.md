## Softmax

1. Softmax is a straightforward extension of logistic regression for multi-class classification. Softmax activation takes a whole vector as input and outputs a vector of the same size. This is in contrast to ReLU or sigmoid which work on a single real number.(When applied to vectors, they do it element-wise i.e on single random numbers. In contrast, softmax uses the entire vector)

2. $g(z)=\frac{\large{e^{z}}}{\sum_{i=1}^{C}{e^{\large{z_i}}}}$ 

3. When C=2, one can see that it is equivalent to logistic regression best explained by [this](https://stackoverflow.com/a/43174772) StackOverflow answer.

4. The cost function that is used here if softmax is the last layer(which it usually is, because that's the whole point) is:

   $\sum_{i=1}^{C}{-y^{(i)}\log{(\hat{y}^{(i)}})}$

5. However, my personal opinion is, it should be:

   $\sum_{i=1}^{C}{-y^{(i)}\log{(\hat{y}^{(i)})}-(1-y^{(i)})\log{(1-\hat{y}^{(i)}})}$

6. This is because the first one penalizes non-adherance to $y^{(i)}$ only if $y^{(i)}$ is $1$ ! If $y^{(i)}$ is $0$, then no matter how bad $\hat{y}^{(i)}$, there's no penalty. This won't give a very good model. If we penalize this too, as done in my second cost function, then we will get sharper results I think.

