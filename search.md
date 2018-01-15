#Search
I missed the first two lectures of this topic.

Time-space complexity, completeness, and optimality are things that we need to consider when picking search parameters.
##Breadth-First Search
Two parameters, $$b$$ and $$d$$. High time and space complexity, $$b^{d+1}$$.

## Uniform-Cost Search
There are costs of different values on the transition factors.

We want to sort things on the frontier. To find the optimal-cost solution, we sort things on the frontier by the lowest cost paths that we constructed. Always expands the least cost path. It is identical to breadth first if each action has identical cost.

Intuitively, "search everything at cost 1, then search everything at cost 2"

**Completeness**: If each transition has non-zero positive cost, the previous argument for breadth first holds.

**Optimality**: Finds optimal solution if you have non-zero positive cost.

###Lemma 1
Let c(n) be the cost of node n on OPEN. If n2 is expanded immediately after n1, then $$c(n1)\leq c(n_2)$$
###Lemma 2
When node n is expanded, every path in the search space with cost strictly less than $$c(n)$$ has already been expanded.
###Lemma 3
The first time uniform-cost expands a node n terminating at state S, it has found the minimal cost path to S.


**Complexity**: $$O(b^{\frac{C^*}{\epsilon}+1})$$ where $$C^*$$ is the cost of the optimal solution, $$\epsilon$$ is the minimal cost of an action, each transition has and non-zero positive costs.

Note that the cost of sorting (inserting in the frontier) will add to complexity, though it is dominated by the above.

##Depth-First Search
Place the successors of the current state at the **front** of the frontier, so you always expand to the deepest node in the frontier.

**Completeness**: It is complete under the following circumstances:
1. Cycle detection
2. Finite number of paths

**Optimality**: Not guaranteed to be optimal! When it reaches the target for the first time, it will stop.


**Time Complexity**: Complexity in time is $$O(b^m)$$ where $$m$$ is the length of tthe longest path in the state space. It can be really bad if $$m$$ is large, but usually it's alright.

**Space complexity** is $$O(bm)$$, it is in linear space! The frontier only contains the deepest node on the current path and the backtrack points.

**Backtrack points**: unexplored siblings of nodes along the current path.

##Depth-Limited Search
Put a limit on your depth-first search to limit the $$m$$, which guarantees your worst case time complexity. It will only find a solution if a solution of $$length\leq L$$ exists.

##Iterative Deepening Search
Starting with depth limit L=0, iteratively increase the depth limit and keep searching.

This sounds like a dumb idea but it actually is not. If you can avoid going another step deeper into the frontier, you save a lot of time.

**Completeness**: yes it is complete!

**Time complexity**: $$O(b^d)$$, check [slides page 78](http://www.teach.cs.toronto.edu/~csc384h/winter/Lectures/csc384w18-Lecture02-UninformedSearch.pdf) for breakdown.

##Path and Cycle Checking
