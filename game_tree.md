##Quick Review
Say you have the following evaluation function: $$f(n) = (2-w) * g(n) + w*h(n)$$. It performs:
* A* search if $$w=1$$
* Greedy best-first if $$w=2$$
* Uniform cost if $$w=0$$

There is an intuitive example in the [lecture slides](http://www.teach.cs.toronto.edu/~csc384h/winter/Lectures/csc384w18-Lecture03-Games.pdf), page 3.

A* search is optimal (will eventually find the right solution) if the heuristic is **admissible**. It also takes less steps if it is **consistent**.

##Game Tree Search
So far, our search problems have been deterministic, where we have full control of the environment. Our environment in real life can be **stochastic**, there may be other agents with clashing interests, and optimal paths can change based on the actions of the other agents.

We will look at games where there are rational opponents. The opponents make decisions to maximize their gain based on their goals. Games are hard because both agents' actions depend on each other.

### Game Properties
* **Two-player**: agent and opponent
* **Discrete**: games states or decisions can be mapped on discrete values
* **Finite**: only finite number of states and decisions
* **Zero-sum**: one player wins, the other loses an equal amount.
* **Deterministic**: no chance involved
* **Perfect information**: all aspects are fully observable

Definitions for **Two-Player Zero-Sum Game**:
* Two players, A (Max) and B (Min)
* Set of states $$S$$
* An initial sstate $$I\in S$$
* Terminal positions $$T \subseteq P$$
* Successor functions that take a state as input and returns a set of possible next states.
* Utility or payoff function mapping terminal states to a utility

Intuitively, players alternate moves, and game ends when a terminal state is reached. A game state is a state-player pair (whose turn it is).

**Missed a whole lecture here, up to slide 50**.
We generate a Minimax tree, expanding the whole thing down to the terminal. It also assumes the opponent is rational and maximizes their gain.
###Pruning
We can make alpha and beta cuts. It just gets rid of the useless parts. The algorithm is similar to the algorithm used to generate the tree. The alpha and beta variables propagate down the tree.

If you are at a beta node, you update and compare your beta variable against the alpha variable handed by the parent. Rule is reversed if you are at an alpha node.

A cutoff is warranted if $$\alpha \geq \beta$$. This says something about the optimal ordering of the children. We can make guesses (heuristics) to invoke more cutoffs.

Alpha beta pruning: depth first?

If the move ordering is optimal (best move searched first), the pruning reduces the effective number of layers by a factor of 2.

###Expectimax Search
Minimax might be too conservative, ensures you do as well as possible in the worst case. Consider probabilistic opponents where they have some randomness in their actions.

###Practical matters
You can't really enumerate real games because they're big! You can't expand all the way to terminal nodes. You should make heuristic estimates about the values of the non-terminal states at the leaves. These heuristics are **evaluation functions**, and they are often learned.

Also there is issues with search - don't go too deep because you may run out of time and memory. Often it's smart to dynamically decide how deep you search.
