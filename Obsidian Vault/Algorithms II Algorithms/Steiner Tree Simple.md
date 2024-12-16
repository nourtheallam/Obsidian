We can compute the Steiner tree of a subset $K$ through the following steps: 

1. Calculate all possible subsets of $V$
2. For all subsets $V' \supseteq K$, calculating the MST of $V'$ (in polynomial time). 
3. Search for the minimum of the minimum spanning trees and report.

Since there are $2^n$ subsets, this algorithm takes $O^*(2^n)$ time.