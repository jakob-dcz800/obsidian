# Converting to a DFA

## Subset construction

## Example

We have our sets from the [[epsilon closure]].

| DFA State | Epsilon closure              | Set                         |
| --------- | ---------------------------- | --------------------------- |
| E         | $\hat{\epsilon}(Ø)$          | $\set{Ø}$                   |
| S         | $\hat{\epsilon}(\set{1})$    | $\set{1, 2, 5, 6, 7}$       |
| A         | $\hat{\epsilon}(\set{8})$    | $\set{1, 2, 5, 6, 7, 8}$    |
| B         | $\hat{\epsilon}(\set{3, 8})$ | $\set{1, 2, 3, 5, 6, 7, 8}$ |
| C         | $\hat{\epsilon}(\set{4})$    | $\set{4}$                   |

## Tradeoff

![[Pasted image 20260611154256.png]]
