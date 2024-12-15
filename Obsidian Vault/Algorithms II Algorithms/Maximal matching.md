Inspect every edge in the graph. 

If neither of its endpoints are unmatched, add it to the matching.

This can be done in $O(n+m)$ time as we can mark every vertex as unmatched in $O(n)$ time then inspect every edge in $O(m)$. 