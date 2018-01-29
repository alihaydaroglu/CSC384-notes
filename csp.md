#Constraint Satisfaction Problems

We've been doing work to put our problems into specific state representations to put them in search problems.

Some search problems, we don't care about the path but just the goal. Most CSPs just care about how we get to the goal configuration. CSPs use a generalized state representation.

##State Representation
We have a set of features, each of which have a set domain. You can specify partial states. CSPs search for a set of values of the features that satisfy some conditions/constraints.

Example is Sudoku.

Constraints are encoded as something that takes in a state and returns T/F.

Each constraint has a scope (the variables it cares about). You can have unary, binary or higher-order constraints based on the size of its scope.

A solution is an assignment of each variable s.t. all constraints are satisfied.

##Graphs
Nodes represent variables, and the edges are the constraints.
