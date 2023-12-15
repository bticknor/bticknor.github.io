# A Measure-Theoretic Look at LOTUS

The Law of the Unconscious Statistician is one of the most useful and "nicest feeling" results in probability.  In fact, it "feels" so nice as to be almost second nature (hence the name).  In an introductory probability class, the law is stated separately for discrete and continuous random variables: 

$$
E[g(X)] = \sum_{x \in supp(X)} g(x) f_X(x)
$$

$$
E[g(X)] = \int_{x \in supp(X)} g(x) f_X(x) dx
$$

However, as with many things in probability, LOTUS can be expressed more generally - i.e. for random variables that are neither discrete nor continuous - using machinery from measure theory.  In fact, LOTUS itself is just a specific case of the general measure-theoretic **change of variables** formula.

Below we prove the general LOTUS and then back-out the specific cases corresponding to continuous and discrete random variables.  This is a worthwhile exercise because it refers us to a number of important concepts from measure theory.

This blog posts assumes some basic knowledge of measure theory.  If you are unfamilar or rusty with these I highly recommend the measure theory YouTube series by [Bright Side of Mathematics](https://www.youtube.com/playlist?list=PLBh2i93oe2qvMVqAzsX1Kuv6-4fjazZ8j).

## Proof of the General LOTUS

Let's first express $E[g(X)]$ in a measure-theoretic context, where:

- $X$ is a random variable mapping from a probability space $(\Omega, F, P)$ into a measurable space $(R, B)$

- $g(R, B) \rightarrow (X, S)$ 

We then have:

$$ E[g(X)] = \int_{\Omega} g(X(\omega)) dP $$

Now assume $g$ to be a positive simple function, such that there exist a collection of disjoint $A_i \in B$ where:

$$g(x) = \sum_i c_i I_{x \in A_i}$$

Then:

$$\int_{\Omega} g(X(\omega)) dP  = \int_{\{\omega \in F | X(\omega) \in \cup_i A_i\}} g(X(\omega))dP + \int_{\{\omega \in F | X(\omega) \notin \cup_i A_i\}} g(X(\omega))dP$$

$$= \int_{\{\omega \in F | X(\omega) \in \cup_i A_i\}} g(X(\omega))dP$$

$$= \sum_i \int_{\{\omega \in F | X(\omega) \in A_i\}} g(X(\omega))dP$$

$$ = \sum_i \int_{\{\omega \in F | X(\omega) \in A_i\}} c_i dP$$
 
$$ = \sum_i c_i P(\{\omega \in F | X(\omega) \in A_i\})$$
 
Let's think for a second about $P(\{\omega \in F \| X(\omega) \in A_i\})$.  This is the probability of the set that $X$ maps to $A_i$. We can express this using the  **pushforward measure** $X^{-1} \circ P$ on $B$, which just measures $A_i$ using the probability of the set in $\Omega$ that $X$ sends to it:

$$ = \sum_i c_i (X^{-1} \circ P)(A_i)$$

$$ = \int_{R} g d(X^{-1} \circ P)$$

We have thus far been assuming that $g$ is a simple function, but remember that by the **simple function approximation lemma** any measurable function $g$ can be approximated arbitrarily well by simple functions.  Therefore there exists a sequence of simple functions $g_n$ such that $lim_{n \rightarrow \infty} g_n = g$.  Thus by the very powerful **monotone convergence theorem** we have that:

$$
lim_{n \rightarrow \infty} \int_{\Omega} g_n(X(\omega)) dP = \int_{\Omega} lim_{n \rightarrow \infty}  g_n(X(\omega)) dP
$$

$$
= \int_{\Omega} g(X(\omega)) dP
$$

$$
= lim_{n \rightarrow \infty} \int_{R} g_n d(X^{-1} \circ P) = \int_{R} lim_{n \rightarrow \infty} g_n d(X^{-1} \circ P)
$$

$$
= \int_{R} g d(X^{-1} \circ P)
$$

And therefore the result holds for all positive measurable $g$ in $L^1 (X^{-1} \circ P)$.  We can extend the result to all measurable functions in $L^1 (X^{-1} \circ P)$ by taking an arbitrary positive and/or negative function, decomposing it into it's positive and negative parts, and following the same process.

Notice that a random variable $X$ is just a measurable function (with no other stipulations), and we didn't use anything "special" about our probability space in this proof that wouldn't also apply to a general measure space.  Therefore what we proved holds for an arbitrary measurable function that maps from any measure space.  The more general result is the **change of variables** formula.

## Recovering the Continuous Case

We have proved the general LOTUS.  However, it is *so* general that it looks quite dissimilar to the continuous random variable LOTUS stated above. How can we recover the specific continuous case from the more general case?

An obvious first step is to take the assumptions about $X$ that are baked into the continuous case and express them in the measure theoretic context.  We assumed that $X$ was a real valued continuous random variable, so we can say that: $X:(\Omega, F, P) \rightarrow (R, B, \lambda)$ where we now fix $R$ as the real numbers, $B$ as the Borel sigma algebra of $\mathbb{R}$, and $\lambda$ as the Lebesque measure.  We are also assuming via the "continuous" designation that the distribution of $X$ - a.k.a. the pushforward measure $X^{-1} \circ P$ on $\mathbb{R}$ - is *absolutely continuous* with respect to the ("reference measure") $\lambda$.  This just means that $\lambda(b) = 0 \implies (X^{-1} \circ P)(b) = 0$ for any $b \in B$.

These specifications and assumptions allow us to do a little bit more with the pushforward measure $X^{-1} \circ P$ of $X$.  Namely, the **Radon-Nikodym** theorem tells us that due to the absolute continuity of the pushforward measure with respect to $\lambda$, there exists a measurable function $f: \mathbb{R} \rightarrow \mathbb{R}$ such that:

$$
(X^{-1} \circ P)(A_i) = \int_{A_i} f d\lambda
$$

For our continuous random variable $X$, this function $f$ is indeed the density function $f_X$.  Notice that we have seen the expression $(X^{-1} \circ P)(A_i)$ before!  Above, when we assumed $g$ to be a simple function we got to:

$$E[g(X)] = \sum_i c_i (X^{-1} \circ P)(A_i)$$

"Plugging in" our assumptions and using the Radon-Nikodym theorem yields:

$$= \sum_i c_i \int_{A_i} f d\lambda $$

$$ = \sum_i \int_{A_i} c_i f d\lambda = \int_{\mathbb{R}} g f d\lambda = \int_{\mathbb{R}} g(x) f_X(x) dx $$

That formula looks familiar!

## Recovering the Discrete Case

Now suppose that $X$ is a discrete random variable.  Then $X:(\Omega, F, P) \rightarrow (R, B, \mu)$ is a measurable function that maps into a *countable* range $R$.  Let's suppose that $B$ is the power set of $R$ (which is indeed a sigma algebra), and $\mu$ is the counting measure defined on $B$ (i.e. $\mu(A_i) = \|A_i\|$).  Then we have that the induced measure $X^{-1} \circ P$ is absolutely continuous with respect to $\mu$, and therefore by Radon-Nikodym we have that $(X^{-1} \circ P)(A_i) = \int_{A_i} f d \mu$.  You have probably guessed what $f$ is here - it's the probability mass function of $X$.  Therefore, $\int_{A_i} f d \mu = \sum_{x \in A_i} f(x)$.  Then, as above:

$$
E[g(X)] = \sum_i c_i (X^{-1} \circ P)(A_i)
$$

$$
= \sum_i c_i \int_{A_i} f d \mu
$$

$$
= \sum_i c_i \sum_{x \in A_i} f(x)
$$

$$
= \sum_i \sum_{x \in A_i} c f(x)
$$

$$
= \sum_{x \in R} g(x)f_X(x)
$$

## Conclusion

The general LOTUS is much stronger than the specific cases that we recovered as it doesn't require the random variable $X$ to be absolutely continuous (we don't need $f_X$ to exist), and it holds for all $L^1$ measurable functions $g$.  Of course, actually computing $E[g(X)]$ for an "exotic" $X$ might be quite difficult!

## References

Rinaldo, A. (2018). Limit Theorems and the Standard MAchinery https://www.stat.cmu.edu/~arinaldo/Teaching/36752/S18/Notes/lec_notes_3.pdf


