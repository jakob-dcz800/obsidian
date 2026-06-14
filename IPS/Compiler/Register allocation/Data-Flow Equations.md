# Data-Flow Equations

For faster convergence compute in reverse: 
`in[i + 1]` before `out[i]`, and `out[i]` before `in[i]` (backward data-flow analysis).
$$
in[i] = gen[i] \cup (out[i] \setminus kill[i])
$$
$$
out[i] = \bigcup_{j \in succ[i]}in[j]
$$

| fib(n) | Instruction                             | `succ[i]` | `gen[i]` | `kill[i]` |
| ------ | --------------------------------------- | --------- | -------- | --------- |
| 1      | `a := 0`                                | 2         |          | `a`       |
| 2      | `b := 1`                                | 3         |          | `b`       |
| 3      | `z := 0`                                | 4         |          | `z`       |
| 4      | `LABEL loop`                            | 5         |          |           |
| 5      | `IF n = z`<br>`THEN end`<br>`ELSE body` | 6, 13     | `n, z`   |           |
| 6      | `LABEL body`                            | 7         |          |           |
| 7      | `t := a + b`                            | 8         | `a, b`   | `t`       |
| 8      | `a := b`                                | 9         | `b`      | `a`       |
| 9      | `b := t`                                | 10        | `t`      | `b`       |
| 10     | `n := n − 1`                            | 11        | `n`      | `n`       |
| 11     | `z := 0`                                | 12        |          | `z`       |
| 12     | `GOTO loop`                             | 4         |          |           |
| 13     | `LABEL end`                             | 14        |          |           |
| 14     | `RETURN a`                              |           | `a`      |           |

## In
`in[i]` = variables that must already have a value before instruction `i` executes, because that value may be needed later.

For example, at instruction 6, `z` is not in `in[6]` even though it was assigned earlier, because after the branch decision at instruction 5, the value of `z` is never used along the path through the loop body.

### First iteration

| fib(n) | Instruction                   | `in[i]`      | explained                                                                                                                   |
| ------ | ----------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------- |
| 1      | `a := 0`                      | `n`          | `n` must be available because <br>it is used later in the loop condition <br>and decrement operation.                       |
| 2      | `b := 1`                      | `n, a`       | `n` is needed later; `a` is needed <br>later by `t := a + b` before `a` <br>is redefined.                                   |
| 3      | `z := 0`                      | `n, a, b`    | `n` is needed later; `a` and `b` are <br>needed later by `t := a + b`.                                                      |
| 4      | `LABEL loop`                  | `n, z, a, b` | The next instruction compares `n` <br>and `z`; `a` and `b` may be needed <br>if execution continues into the loop body.     |
| 5      | `IF n = z THEN end ELSE body` | `n, z, a, b` | `n` and `z` are used immediately <br>by the test; on the `body` branch, <br>`a` and `b` are still needed for computing `t`. |
| 6      | `LABEL body`                  | `a, b, n`    | `a` and `b` are needed by the next <br>instruction (`t := a + b`); `n` remains <br>live because it is decremented later.    |
| 7      | `t := a + b`                  | `a, b, n`    | `a` and `b` are used immediately to <br>compute `t`; `n` is still needed later <br>by `n := n - 1`.                         |
| 8      | `a := b`                      | `b, t, n`    | `b` is needed to perform the assignment; <br>`t` will be needed by `b := t`; <br>`n` is needed later.                       |
| 9      | `b := t`                      | `t, n`       | `t` is needed immediately to update `b`; <br>`n` is needed later by the decrement.                                          |
| 10     | `n := n − 1`                  | `n`          | The current value of `n` is needed to <br>compute the new value `n - 1`.                                                    |
| 11     | `z := 0`                      | _(empty)_    | No variable value is required before <br>this instruction; it overwrites `z` with <br>a constant.                           |
| 12     | `GOTO loop`                   | _(empty)_    | The jump itself uses no variables. <br>(Variables become live again only <br>after control reaches instruction 4)           |
| 13     | `LABEL end`                   | `a`          | `a` must be preserved because it is <br>returned immediately afterward.                                                     |
| 14     | `RETURN a`                    | `a`          | `a` is used directly by the return statement.                                                                               |
One subtle point: **`in[i]` is not "variables assigned previously."** It is **"variables whose current values are still needed."**
## Out
**`out[i]`** = variables that must have correct values **immediately after** instruction `i`.

>[!TIP]
>The `out[i]` sets are the union of the `in[i]` sets of the instructions successors:
>$$
out[i] = \bigcup_{j \in succ[i]}in[j]$$


| fib(n) | Instruction                   | `in[i]`      | `succ[i]` | `out[i]`     | Explainer               |
| ------ | ----------------------------- | ------------ | --------- | ------------ | ----------------------- |
| 1      | `a := 0`                      | `n`          | 2         | `n, a`       |                         |
| 2      | `b := 1`                      | `n, a`       | 3         | `n, a, b`    |                         |
| 3      | `z := 0`                      | `n, a, b`    | 4         | `n, z, a, b` |                         |
| 4      | `LABEL loop`                  | `n, z, a, b` | 5         | `n, z, a, b` |                         |
| 5      | `IF n = z THEN end ELSE body` | `n, z, a, b` | 6, 13     | `a, b, n`    | `a` is both in 6 and 13 |
| 6      | `LABEL body`                  | `a, b, n`    | 7         | `a, b, n`    |                         |
| 7      | `t := a + b`                  | `a, b, n`    | 8         | `b, t, n`    |                         |
| 8      | `a := b`                      | `b, t, n`    | 9         | `t, n`       |                         |
| 9      | `b := t`                      | `t, n`       | 10        | `n`          |                         |
| 10     | `n := n − 1`                  | `n`          | 11        | _(empty)_    |                         |
| 11     | `z := 0`                      | _(empty)_    | 12        | _(empty)_    |                         |
| 12     | `GOTO loop`                   | _(empty)_    | 4         | _(empty)_    |                         |
| 13     | `LABEL end`                   | `a`          | 14        | `a`          |                         |
| 14     | `RETURN a`                    | `a`          |           | _(empty)_    |                         |

## Further iterations

>[!TIP]
>$$
in[i] = gen[i] \cup (out[i] \setminus kill[i])
$$


| `succ[i]` | `gen[i]` | `kill[i]` | `out[i]:1`   | `in[i]:2`    | explained                         |
| --------- | -------- | --------- | ------------ | ------------ | --------------------------------- |
| 2         |          | `a`       | `n, a`       | `n`          |                                   |
| 3         |          | `b`       | `n, a, b`    | `n, a`       |                                   |
| 4         |          | `z`       | `n, z, a, b` | `n, a, b`    |                                   |
| 5         |          |           | `n, z, a, b` | `n, z, a, b` |                                   |
| 6, 13     | `n, z`   |           | `a, b, n`    | `n, z, a, b` |                                   |
| 7         |          |           | `a, b, n`    | `a, b, n`    |                                   |
| 8         | `a, b`   | `t`       | `b, t, n`    | `a, b, n`    | `t` is in `kill` and not included |
| 9         | `b`      | `a`       | `t, n`       | `b, t, n`    |                                   |
| 10        | `t`      | `b`       | `n`          | `t, n`       |                                   |
| 11        | `n`      | `n`       | _(empty)_    | `n`          |                                   |
| 12        |          | `z`       | _(empty)_    |              |                                   |
| 4         |          |           | _(empty)_    |              |                                   |
| 14        |          |           | `a`          | `a`          |                                   |
|           | `a`      |           | _(empty)_    | `a`          |                                   |

