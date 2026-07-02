# Ejercicio 3

Las restricciones de andersen van a ser: 

1. $\{O1\} \subseteq L(b1)$
2. $\{O2\} \subseteq L(b2)$
3. $\{OA\} \subseteq L(oA)$
4. $\{OB\} \subseteq L(oB)$
5. $L(oA) \subseteq \cap \{E(k, \text{value} | k \in L(b1))\}$
6. $L(oB) \subseteq \cap \{E(k, \text{value} | k \in L(b2))\}$
7. $L(b2) \subseteq L(b1)$
8. $\cup \{E(k, \text{value} | k \in L(b1))\} \subseteq oC$

Por lo tanto: 

- $L(b1) = \{O1, O2\}$
- $L(b2) = \{O2\}$
- $L(oA) = \{OA\}$
- $L(oB) = \{OB\}$
- $L(oC) = \{OA, OB\}$
- $E(O1, \text{value}) = \{OA\}$
- $E(O2, \text{value}) = \{OA, OB\}$

