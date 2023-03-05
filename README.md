# Bayesian-Machine-Learning-Tasks

## Task 1 Frechet Distribution Output Plot:



![image](https://user-images.githubusercontent.com/77116750/222972533-e09cb6d2-c079-424e-8c98-78e91b4832b7.png)


## Task 2:

 i) Cross-entropy: Cross-entropy measures the difference between two probability distributions p and q. In machine learning, it is often used as a loss function to train classification models. The cross-entropy between two probability distributions p and q is defined as:

$$ H(p, q) = -\sum_{i}p(i)\log q(i) $$

where i ranges over all possible events.

ii) Entropy: Entropy measures the amount of uncertainty or randomness in a probability distribution. The entropy of a discrete probability distribution p is defined as:

$$ H(p) = -\sum_{i}p(i)\log p(i) $$

where i ranges over all possible events.

iii) Mutual information: Mutual information measures the amount of information shared between two random variables. It is defined as:

$$ I(X; Y) = H(X) - H(X|Y) $$

where X and Y are two random variables.

iv) Conditional entropy: Conditional entropy measures the amount of uncertainty in a random variable given another random variable. The conditional entropy of a random variable X given another random variable Y is defined as:

$$ H(X|Y) = \sum_{j}p(Y=j)H(X|Y=j) $$

where j ranges over all possible values of Y.

v) KL divergence: KL divergence measures the difference between two probability distributions p and q. It is defined as:

$$ D_{KL}(p||q) = \sum_{i}p(i)\log\frac{p(i)}{q(i)} $$

where i ranges over all possible events.

Refer to Task 2 file for code and implementations

## Task 3:

Results:
Random Forest: 0.88

## Task 4:

## Task 5:
Refer to Task 5 file

## Task 6:

Plot of (left) Forward KL Divergence and (right) Reverse KL Divergence:


![image](https://user-images.githubusercontent.com/77116750/222972697-b0820cdf-d28f-4cdd-a8bc-3d958aa26981.png)

## Task 7:

We can use Bayes' rule to calculate the posterior distribution of the coin that we picked up, given the observed data. Let C denote the event that we picked up coin c, and let D denote the event that we observed the sequence of tosses D=[H, T, H, H, T, H, H, H, H, H].

Then, using Bayes' rule, we have:

P(C|D) = P(D|C) * P(C) / P(D)

where P(D|C) is the likelihood of observing the sequence of tosses given that we picked up coin c, P(C) is the prior probability of picking up coin c, and P(D) is the probability of observing the sequence of tosses averaged over all possible coins.

We know that the prior probability P(C) is uniformly distributed over all coins, so P(C) = 1/N, where N is the total number of coins in the box. We also know that the likelihood function for the Kumaraswamy distribution with a=2 and b=3 is:

P(D|C) = B(3+5, 2+5) * (1/2)^5 * (1/3)^5

where B is the beta function, and we use the fact that the number of heads and tails in the sequence are 8 and 2 respectively.

The denominator P(D) can be calculated using the law of total probability:

P(D) = ∑ P(D|C) * P(C) over all possible coins

Since the prior is uniform, we can simplify this as:

P(D) = (1/N) * ∑ P(D|C) over all possible coins

We can compute this sum by sampling from the Kumaraswamy distribution with a=2 and b=3 for each possible coin, and averaging over the results. However, this is a computationally expensive task and might not be feasible for a large number of coins.

Therefore, we will skip the calculation of P(D) and focus on the numerator and denominator ratio, which gives us the posterior distribution up to a normalizing constant:

P(C|D) ∝ P(D|C) * P(C)

Substituting the expressions for P(D|C) and P(C), we have:

P(C|D) ∝ B(3+5, 2+5) * (1/2)^5 * (1/3)^5 * (1/N)

which simplifies to:

P(C|D) ∝ (27/512) * B(8, 7) / N

where B(8, 7) is the beta function with parameters 8 and 7. Note that the expression on the right-hand side depends only on the number of coins N, and not on the specific values of the parameters a and b of the Kumaraswamy distribution.

Since the posterior is proportional to a beta distribution with parameters 8 and 7, we can normalize it to obtain the exact posterior distribution:

P(C|D) = B(8, 7) / B(3+5, 2+5) * (1/2)^5 * (1/3)^5 * (1/N)

which is a beta distribution with parameters a=8 and b=7.

Therefore, the probability distribution of the coin that we picked up is a beta distribution with parameters a=8 and b=7.

Refer to Task 7 file for Code(part b)

Output of (b)
sample: 100%|██████████| 3000/3000 [00:08<00:00, 338.94it/s, 3 steps of size 9.78e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 844.63it/s, 1 steps of size 8.65e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 835.32it/s, 3 steps of size 8.68e-01. acc. prob=0.95] 
sample: 100%|██████████| 3000/3000 [00:04<00:00, 632.25it/s, 1 steps of size 8.73e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:04<00:00, 670.32it/s, 3 steps of size 1.08e+00. acc. prob=0.89] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 848.20it/s, 1 steps of size 8.71e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 839.66it/s, 1 steps of size 8.56e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:05<00:00, 511.43it/s, 3 steps of size 8.43e-01. acc. prob=0.94] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 839.66it/s, 1 steps of size 9.34e-01. acc. prob=0.93] 
sample: 100%|██████████| 3000/3000 [00:03<00:00, 827.80it/s, 3 steps of size 8.29e-01. acc. prob=0.94] 


![image](https://user-images.githubusercontent.com/77116750/222972796-0d909010-0b1e-4848-923e-8d41ff460d47.png)



