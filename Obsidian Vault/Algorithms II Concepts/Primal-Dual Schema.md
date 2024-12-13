**For non [[NP-Hard]] problems:** 

An algorithm that solves a problem using the primal-[[Dual]] schema maintains a primal solution of the problem's LP, ad a [[Dual]] solution of its corresponding [[Dual]]

1. The [[Dual]] solution is always **feasible**.
2. The primal solution is always satisfies some **optimality** criterion, such as [[Complementary Slackness]].

The algorithm iteratively updates the primal and [[Dual]] solutions such that the primal becomes feasible while maintaining the above conditions.

Once the primal is feasible, both solutions must be optimal because they satisfy the optimality criterion ([[Complementary Slackness]]).

**For [[NP-Hard]] problems:**

We follow the same steps, but instead of satisfying [[Complementary Slackness]] (which would thus imply P = NP), they satisfy [[Relaxed Complementary Slackness]], thus making the primal an $\alpha \beta$-[[Approximation]]. 