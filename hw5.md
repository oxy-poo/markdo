# 1
## Part 1
General Idea: We do a breadth first search of all the nodes, but we only explore the node if it is reachable. We add all reached nodes to a solution set. We compare the solution set to the set of Vertices and if they are equal, then we can reach every point. Let S be the source node. Let us have 3 sets, white, grey, and black

```
Route-Exists(V,E,S):
	for U : every non-source vertex
		white.push(u)
		u.prev = null
	// Q is a FIFO data structure
	Q = empty
	Enqueue(s)
	while Q not empty
		u = Dequeue(Q)
		for v:  each neighbor:
			if(v is white && length to neighbor <= L)
				white.remove(v)
				gray.push(v)
				v.prev = u
				Enqueue(u)
		black.push(u)
	if(black != V) return false
	else return true
```
Here, we iterate through the vertices twice, and evaluate all edges, giving us O(2V + E), or O(V + E).
## Part 2
We must use a modified version of Dijkstra's Algorithm. Let S be the source node.
```
mod-Dijkstra(V,E,S):
	Dist[v]
	S[v]
	create vertex set Q
	for each vertex v in Graph:
		dist[v] = +inf
		prev[v] = null
		add v to Q
	dist[source] = 0
	prev[source] = source
	while Q not empty:
		u = vertex with min dist[u]
		remove u from Q
		max_weight = +inf
		for each neighbor v of u in Q:
			tmp =  weight of (u,v)
			if( tmp < max_weight):
				max_weight = tmp
				prev[v] = u
	return max_weight
```
This has the same run time as Dijkstra's with but instead of calculating the shortest path, we minimize maximum weight. 

# 2
The definition of minimum spanning tree is a set of minimum edges that connects T. 
The algorithm works because we organize the graph from highest weight to lowest weight and then we delete non-critical edges starting from the front. This will delete all sub-optimal edges in the minimum spanning tree. 
The algorithm is logically equivalent to Kruskal's algorithm but works in reverse.
# 3
The brute force algorithm takes 2^n time, because we the possible inputs we must choose from is the power set of the edges. A very slow algorithm for doing this would be:
```
Max Clique(V,E):
	Generate the Powerset A for V which takes 2^V time.
	max_size = 1
	for each Set S in A:
		for i in Set S
			for j = i in Set S
				if no edge [i,j]
					continue to next set
		
		if max_size < |S|
			max_size = |S|
	return max_size
					
```
Generating through the powerset would take 2^n^. Iterating through this set would take E times because of the number of edges. This algorithm would take O(2^V^ + 2^V^ * E^2^)
# 4
The matrix chain multiplication problem belongs to P class because it solves problem in n^3^ .
# 5
Basically, a vertex cover set is the minimum number of vertices such that each edge is connected to the one of the vertices in the vertex cover set. To verify this, we need to look at all the edges and confirm that 1 of the edges is in the vertex cover set. If I do this in polynomial time, it belongs in NP. L is a list of edges in the pair <v1,v2> and V is the cover set in a with logarithmic access time (tree). Find returns true or false based on whether it exists in the set.
```
V_cover_set_verification(L,V):
	for i in L:
		if( V.find(i.first) NAND V.find(i.second))
			return false
	return true
			

```
The time complexity of this algorithm is O(E*log(V)), which means it exists in NP.
# 6
We know that clique exists in NP.  The relationship can be described as R > Max Clique(exists in NP) > Q. Q is not an NP hard problem. Because of this, we can say that Q is NP complete.  R is at least NP Complete because Max Clique is NP and R is reducible to Max Clique. R is NP must be NP hard. 
# 7

 1. R is NP complete
 2. Q is NP hard
