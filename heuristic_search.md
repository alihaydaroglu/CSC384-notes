#Heuristic Search
A smarter (?) way to search.
##Introduction
Let's try to look ahead to the goal, and see if we can guess the merit of nodes without searching blindly as we did in *uninformed* search.

The notion of **merit** is different
* Optimized for the cost of solution
* Optimize for minimizing computation
* Optimize for the cost of a solution

###Heuristic Function

The idea is to develop a domain specific **heuristic function** $$h(n)$$ which guesses the cost of getting to the goal from node n. It must be *domain specific*.

For example, in the case of the train example, the heursitic function could be something about the distance in a straight line between the two cities.

![2-crow_heuristic](/assets/2-crow_heuristic.JPG)

With a heuristic function, if $$h(n_1)<h(n_2)$$ means we guess that it is cheaper to get to the goal through $$n_1$$.

##Greedy Best-First Search
Always look ahead, never look at the cost. Always use $$h(n)$$ to rank the nodes on the frontier, and always expand to the node with the lowest $$h$$. It's a greedy way to get a low cost solution.

The method ignores the cost of getting to $$n$$, so nodes that cost a lot but have good heuristic values will mess it up.

It is **incomplete** and often **suboptimal**.

##A* Search
Define an **evaluation function**: $$f(n) = g(n) + h(n)$$

Where $$g(n)$$ is the cost of the path to node $$n$$, and $$h(n)$$ is the heuristic estimate of getting from $$n$$ to the goal node.

##Properties of Heuristic Functions
###Admissibility
We always assume that an admissible heuristic underestimates the true cost to reach the goal, it is *optimistic*. So, if $$h^{*}(n)$$ is the cost of the optimal path to a node, then for any node $$h(n)\leq h^{*}(n)$$. We can't always guarantee admissibility. Sometimes we use two heuristics, one of which is admissible to use some sort of branch and bounds? Something along the lines of upper and lower bounding the solution.
