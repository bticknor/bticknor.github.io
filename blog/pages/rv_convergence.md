# Convergence in Probability vs. Almost Sure Convergence - A Visual Explanation

By definition, a sequence of random variables $X_n$ converges to $X$ in probability if:

$$lim_{n \rightarrow \infty} P(|X_n - X| > \epsilon) = 0$$

The sequence converges to $X$ almost surely if:

$$
P(\omega \in \Omega | lim_{n \rightarrow \infty} X_n(\omega) = X(\omega)) = 1
$$

or equivalently:

$$
P(\omega \in \Omega | lim_{n \rightarrow \infty} X_n(\omega) \neq X(\omega)) = 0
$$

These statements look somewhat similar at first glance, but they are describing different notions of what it means for a sequence of random variables to converge.  Here we look at a particular sequence of random variables $X_n$ that converges in probability but not almost surely, and use a visualization to build some intuition for what each of these definitions really means.

# An Example Sequence $X_n$ 

Let $U \sim Uniform(0, 1)$, and define the sequence of random variables $X_n$ like so:

$X_1 = U + I_{[0, 1]}(U)$

$X_2 = U + I_{[0, \frac{1}{2})}(U)$

$X_3 = U + I_{[\frac{1}{2}, 1]}(U)$

$X_4 = U + I_{[0, \frac{1}{3})}(U)$

$X_5 = U + I_{[\frac{1}{3}, \frac{2}{3})}(U)$

$X_6 = U + I_{(\frac{2}{3}, 1]}(U)$

$X_7 = U + I_{[0, \frac{1}{4})}(U)$

...

For $n \in \mathbb{N}$, where $I_A(U)$ is the indicator function that takes value $1$ when $U \in A$ and $0$ otherwise.  What is this sequence doing?  We can see that for any fixed value of $u$, the sequence will oscillate between $u$ and $u + 1$, jumping upwards by 1 at all values of $n$ for which $u$ "turns on" the indicator function associated with $X_n$.  We might describe the behavior of $X_n$ by saying that as it moves forward in $n$ it is scanning over the unit interval from left to right over and over again and "looking" for $u$.  The plot below shows the values of $X_n$ for $n=1,2, ..., 50$ for $u = \frac{\pi}{4}$.

Notice the following two properties of the sequence $X_n$ that we've constructed:

- 1) **The sequence finds any value of $u$ less and less frequently as n increases**

As it progresses, the sequence uses a finer and finer window with which to scan over the unit interval.  Therefore, each scan will take longer (in terms of number of elements of the sequence) and $u$ will still only be found once per scan.

- 2) **The sequences always eventually finds any $u$ again - it therefore finds $u$ "infinitely often"**

Even though the sequence finds $u$ less and less frequently, each scan that it makes covers the entire unit interval.  Therefore it will always find $u$ again, even though it will take longer and longer to do so.  We can say that $X_n$ finds $u$ "infinitely often" in the sense that there does not exist a large enough $n^*$ such that $X_n$ doesn't find $u$ for all $n > n^*$.

# Visualizing the Relationship Between $X_n$ and $U$

We can visualize what $X_n$ is doing in relation to $U$ by building a table (of sorts) with elements of $X_n$ as the rows and possible values of $U$ as the "columns."  Since $U$ takes an uncountable number of values, the "column" values for each row will just be the unit interval.  On each of these  intervals we highlight in red the region for which $X_n$ "finds" $U$, which is the region where $X_n \neq U$ and thus $X_n - U = 1$. This visualization nicely illustrates $X_n$'s behavior of continuously "scanning" across the unit interval with a progressively smaller window.  




