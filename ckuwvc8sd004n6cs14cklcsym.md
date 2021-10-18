## P-value in DoWhy Refutation Test

 In DoWhy's [causal refuter module](https://github.com/microsoft/dowhy/blob/master/dowhy/causal_refuter.py), the developers give a brief introduction in ```test_significance``` 
regarding p-value interpretation:

```
#The basis behind using the sample statistics of the refuter when we are in fact testing #the estimate, is due to the fact that, we would ideally expect them to follow the same #distribition
#For refutation tests (e.g., placebo refuters), consider the null distribution as a #distribution of effect estimates over multiple simulations with placebo treatment, and #compute how likely the true estimate (e.g., zero for placebo test) is under the null. If #the probability of true effect estimate is lower than the p-value, then estimator method #fails the test.
#For sensitivity analysis tests (e.g., bootstrap, subset or common cause refuters), the #null distribution captures the distribution of effect estimates under the "true" dataset 
#(e.g., with an additional confounder or different sampling), and we compute the #probability of the obtained estimate under this distribution. If the probability is lower #than the p-value, then the estimator method fails the test

#Null Hypothesis: The estimate is a part of the distribution
#Alternative Hypothesis: The estimate does not fall in the distribution.
``` 

It is basically saying:


- For Placebo refuters, if p-value < 0.05 (or any other specified threshold), zero (the expected/true treatment effect) is very unlikely (<5%) to be covered by the generated placebo distribution, thus the ESTIMATOR (yeah, the upper-level estimator) fails the test.

The developer gives a  [better explanation](https://github.com/microsoft/dowhy/issues/312)  in response to an issue:


> For a refutation test, the p-value denotes whether the test has found a problem with the estimate. If p-value <0.05, this means that the estimate has a problem. If not, then we cannot conclude anything.

>Since both p-values are >0.05, it means that the two tests are unable to find a problem in the estimate. Note that refutations test the correctness of the estimating procedure, but not whether the effect is significantly away from zero.

>...

>For placebo test, the p-value measures whether the obtained new effect is significantly different from 0 (since 0 is the correct effect value for a random "placebo" treatment). Since the p-value is > 0.05, it means we cannot conclude that new effect is different from 0.





