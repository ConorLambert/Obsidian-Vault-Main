[Source](https://exercism.org/tracks/csharp/exercises/dominoes)

# Reflection 
- If a side of the domino matches, we use the other side of that same domino in subsequent iterations.
- The variable state holds both sides of a domino that require matching
- It is not associated with any particular domino apart from the first iteration through.
- When a domino is found that matches one side of the variable state, that side of the variable sate

{ (1, 2), (2, 3), (3, 1), (2, 4), (2, 4) }

(1, 2) = (1, 2)
(2, 3) = (1, 3)
(3, 1) = (1, 1)
(2, 3) = (1, 1)
(1, 2) = (1, 3)
(1, 2) = (3, 1)
(2, 4) = (1, 2)
(2, 4) = (1, 4)
(2, 4) = (1, 2)
(2, 4) = (1, 2)
(2, 4) = (1, 4)
(1, 2) = (1, 4)
(1, 2) = (1, 2)
(1, 2) = (1, 1)


