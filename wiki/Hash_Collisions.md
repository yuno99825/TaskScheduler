# Hash Collisions

The `hashcode()` method on a set returns an integer which can represent the hash code value for that set.
 
The hash code of a set is the sum of the hash codes of the elements in the set. This
ensures that `s1.equals(s2)` implies that `s1.hashCode()==s2.hashCode()` for any two sets `s1` and `s2`.
If two sets are equal, they will always return the same hash code. However, it is also possible
that two fundamentally different sets `x1` and `x2` return the same hash code.

Thus, with a sufficiently sized input graph, it is inevitable that different partial schedules return the same
hash code due to the pigeonhole principle. As such, it is possible that the solution incorrectly prunes
large sections of the graph which could contain the optimal solution.

Despite this, we have decided to use hash codes for duplication detection in our solution for the following reasons:

- Given the relatively small nodes and processors the solution is expected to be run on, the likelihood
of a scenario in which _all_ optimal schedules in the graph are incorrectly detected as duplicates
is minimal.

- The solution run time is significantly improved through the use of state duplicate avoidance
via hash codes.

- Our implementation of state duplicate avoidance is easily detachable from the rest of the solution
if the client wishes to forego the sizable speed increase.
