$\rightarrow$ For $G$ to be a cluster graph, it has to have at least the following 

![[Pasted image 20241216110120.png]]


$\rightarrow$ Once we find this triple, we can either remove $(u,v)$, remove $(w,v)$, or add $(u,w)$, giving us a branching vector of $(1,1,1)$. 
![[Pasted image 20241216110252.png]]
$\rightarrow$ This yields a branching number of $3$, and since we bound our depth by $k$, a total running time of $O^*(3^k)$. 
