# Asymptotic vs. Limiting Variance

## Definitions

Suppose that $T_n(X)$ is an estimator of $\tau(\theta)$, for $\theta \in \mathbb{R}$.  Then, the **limiting variance** of $T_n(X)$ is the constant $c$ such that:

$$
lim_{n \rightarrow \infty} \; k_n Var (T_n(X)) = c
$$

For some sequence of constants $k_n$.  The **asymptotic variance** of $T_n$ is defined as the constant $\sigma^2_\theta$ such that:

$$
k_n (T_n(X) - \tau(\theta)) \rightarrow^d N(0, \sigma^2_\theta)
$$

## The Difference Between these Definitions

The difference between these two definitions is where we take the limit.  For the limiting variance, we compute the exact variance of the estimator for a given value of $n$ and *then* evaluate the limiting behavior of this quantity.  For the asymptotic variance, we first take the limit (in distribution) of the scaled estimator, and then calculate the variance.  The limiting variance and asymptotic variance are often identical, but the definitions are not equivalent.  Casella and Berger (pg. 470) include a nice example of an estimator $T_n$ for which the limiting variance and asymptotic variance are not the same.

Suppose that $X_i$ are i.i.d. $N(\mu, \sigma^2)$ observations for $i=1, ..., n$.  Let $T_n(X) = \frac{1}{\bar{X}_n}$.  For any positive value of $\sigma^2$ there is some nonzero probability that $\bar{X}_n$ will take values in a neighborhood of $0$ and $T_n(X)$ will explode.  It follows that $Var(T_n) = \infty$ for any value of $n$. 
 However, by the delta method we have that:

$$
\frac{1}{\bar{X}_n} \rightarrow^d N(\frac{1}{\mu}, \frac{\sigma^2}{n \mu^4})
$$

And so $\frac{1}{\bar{X}_n}$ actually converges in distribution to a distribution with a finite variance, even though at no point along the way does $\frac{1}{\bar{X}_n}$ have a finite exact variance.  Therefore, by definition the asymptotic variance of $T_n$ is $\frac{\sigma^2}{\mu^4}$, as:

$$
\sqrt{n} (\frac{1}{\bar{X}_n} - \frac{1}{\mu}) \rightarrow^d N(0, \frac{\sigma^2}{\mu^4})
$$

The intuition behind why the asymptotic variance gives us something finite in this case is that for $\mu \neq 0$, the probability that $\bar{X}_n$ falls in a neighborhood around $0$ becomes vanishingly small for large values of $n$.  Therefore, taking the limit before the computing the variance allows us to "get to" a distribution with a finite second moment before we actually compute the variance.  The asymptotic approximation is practically much more useful.

## References

Casella, G. and Berger, R.L. (2002) Statistical Inference. 2nd Edition, Duxbury Press, Pacific Grove.





