# Decentralised Enterprise Knowledge Graph: Query and Reply experimentations results

## School toy dataset

| CQ                                                                                              | Time (average 10 queries) | Semantic links used | Number of queried types | Number of decomposed queried types | Grouped results |
|-------------------------------------------------------------------------------------------------|---------------------------|---------------------|-------------------------|------------------------------------|-----------------|
| { p \| ∃(∅) ∧ ηp(p) = People ∧ p.Type = "Teacher" ∧ B }                                         | 41.044ms                  | 0                   | 1                       | 1                                  | 0               |
| { p \| ∃(∅) ∧ ηp(p) = People }                                                                  | 41.586ms                  | 2                   | 1                       | 3                                  | 2               |
| { p, pc, c \| ∃(∅) εDE(p, pc, c) ∧ ηp(p) = People ∧ ηp(c) = Class ∧ ξp(pc) = People-Class ∧ B } | 28.304ms                  | 4                   | 3                       | 7                                  | 2               |

## France OpenData



## Team of Teams survey data company

