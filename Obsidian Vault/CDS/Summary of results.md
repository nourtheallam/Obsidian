---
~
---

We evaluated the number of backward steps in relation to K-mer size and the insertion parameter using a filter of size 125K bytes for varying MEM sizes. Results indicate that the number of backward steps peaks when the K-mer size matches the MEM size. Additionally, the most significant reduction in backward steps occurs with MEM sizes of 15 or greater when paired with the largest K-mer size possible, and as the insertion parameter approaches 10 (the maximum tested value). 

We also examined backward steps as a function of filter size for various K-mer, MEM, and insertion parameter values. Interestingly, the number of backward steps increases with filter size when the MEM size equals the K-mer size. Conversely, when the K-mer size is set to 5, the number of backward steps remains unchanged. The most substantial improvements are observed when the insertion parameter is set to 1 and the MEM size exceeds the K-mer size in other cases.