# Top-Down Parsing

Builds [[syntax tree]] from the root going down.
Also called *predictive parsing*: guesses the to-be-used production.
Reads Left-to-right, uses Leftmost derivation, look-ahead 1: [[LL(1)]]

>[!tip]
>Uses a stack to keep track of the derivation sequence.

## Example

We have two productions:
```
T -> aTc
T -> R
```

As long as the input is `b` we choose `T` nr. 2
For input `a` we of course choose the first `T`
This method extends do more productions that start with terminals.
Here, we find the [[first set|first sets]]. These describe the initial characters that each production produce.
To calculate `FIRST` we need a new auxillary function called [[Nullable Property|nullable]]
This indicates if a sequence of grammar symbols $\alpha$ can derive the empty string.

>[!definition]
>$\alpha$ and $\beta$ are sequences of grammar symbols

# Predictive parsing

If the same nonterminal has productions with *disjoint* [[First Set|first sets]], then we can choose the corresponding production if the input char exists in one of the sets. If it doesn't we choose the empty production, if such production exists.

>[!DEFINITION] Generalized rule
>If the next input does **not** exist in any [[first set]], we can choose the [[Nullable Property|nullable]] production.
>Nullable productions can have non-empty first sets, so it can also be chosen if the next input is in its first set.

If there are many nullable productions, we cannot pick one - therefore for predictive parsing, a nonterminal must have at most one nullable production.

[[Follow Set|Follow sets]] are used to choose which nullable nonterminal to choose in predictive parsing.
