# Set 
- empty set: $\emptyset$
- A is subset of  B: $A \subseteq B$
- union of A and B: $A \bigcup B$
- intersection of A and B: $A \cap B$
- complement of A: $A^c$
- De Morgan's laws
$$
\left( A \cup B\right)^{c} = A^c \cap B^c 
$$
$$
\left( A \cap B\right)^{c} = A^c \cup B^c 
$$

---
# Sample Space & Events
## Events and occurrences
- sample space: $S$
- s is a possible outcome: $s \in S$
- $A$ is an event: $A  \subseteq S$
- $A$ occurred: $s_{actual}  \in A$
- something must happen: $s_{actual} \in S$

## New events from old events
- $A$ or $B$ (inclusive): $A \cup B$
- $A$ and $B$: $A \cap B$
- not $A$: $A^c$
- $A$ or B, but not both: $(A \cap B^c) \cup (A^c \cap B)$
- at least one of $A_{1},  \ldots, A_{n}$: $A_{1} \cup \ldots \cup A_{n}$
- all of $A_{1},  \ldots, A_{n}$: $A_{1} \cap \ldots \cap A_{n}$

## Relationships between events
- $A$ implies $B$: $A \subseteq B$
- $A$ and $B$ are mutually exclusive: $A \cap B = \emptyset$
- $A_{1},  \ldots, A_{n}$ are a partition of $S$: $A_{1} \cup \ldots \cup A_{n}$, $A_{i} \cap A_{j} = \emptyset$ for $i \neq j$

---
# Conditional Probability
- the **conditional** probability of $A$ given $B$: $P(A|B)$