# Convergence in Probability vs. Almost Sure Convergence - A Visual Explanation

By definition, a sequence of random variables $X_n$ converges to $X$ in probability if:

$$
lim_{n \rightarrow \infty} P(|X_n - X| > \epsilon) = 0
$$

The sequence converges to $X$ almost surely if:

$$
P(\omega \in \Omega | lim_{n \rightarrow \infty} X_n(\omega) = X(\omega)) = 1
$$

or equivalently:

$$
P(\omega \in \Omega | lim_{n \rightarrow \infty} X_n(\omega) \neq X(\omega)) = 0
$$

These statements look somewhat similar at first glance, but they are describing different notions of what it means for a sequence of random variables to converge.  Here we look at a particular sequence of random variables $X_n$ that converges in probability but not almost surely, and use a visualization to build some intuition for what each of these definitions really means.

