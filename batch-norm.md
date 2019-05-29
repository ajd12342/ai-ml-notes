## Batch Norm

- Batch norm is used to decrease the effect of covariant shift on the later layers in the NN. Covariant shift  happens when the parameters of the NN are trained/updated (for one or more iterations) on a set that has a different distribution than the set on which the parameters are trained next on.
- This happens in intermediate layers in a NN. A given layer $l$ receives $a^{[l-1]}$ as its input. Since one is using a Gaussian transformation, the normalization is effective only if one *assumes a reasonably Gaussian* distribution for the entity that is normalized, either $z^{[l-1]}$ or $a^{[l-1]}$. 
- It seems reasonable to think the former is more Gaussian since $a$ has some non-linearity. Hence, because it is more effective on $z$ the original paper applies BN to $z$. However, my personal(and [Reddit](<https://www.reddit.com/r/MachineLearning/comments/67gonq/d_batch_normalization_before_or_after_relu/>)'s) opinion is that it makes more sense to apply BN after $a$ since the next layer sees $a$, not $z$, so it makes more sense to normalize $a$. There are two issues at hand:
  - It is mathematically correct to apply some BN to $a$ since the input to next layer is to be normalized.
  - The current technique of BN is effective only on $z$ since $z$ has a more Gaussian distribution, intuitively.
  - One can propose a better BN scheme that works on ReLU/sigmoid that in  my opinion will give better results.
- Batch Normalization has a small insignificant regularization effect because of the small noise introduced by the minibatches.
- Batch Normalization helps solve the exploding/vanishing gradient problem by making the distribution of activations at each layer relatively stable which stabilizes the distribution of the weights too.

