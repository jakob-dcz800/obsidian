# Liveness analysis

## Rules for Liveness
1. `var` is **live at the start** of instruction `I` when the value of a variable var is **used** in instruction `I`.
```fsharp
I: a := a + var // var is live at the start
```

2. If `var` is assigned a value in instruction `I` (and (1) does not apply) then `var` is **dead at the start** of `I`.
```fsharp
I: var := b // var is dead at the end
```

3. If `var` is **live at the end** of instruction `I` then it is live at the start of `I` 
	1. (unless `I` assigns to `var`)

4. If `var` is live at the end of instruction `I`, then `var` is **live at the start** of any instruction that may be executed **directly after** `I`.

## Concepts
> We number program instructions from $i = 1$ to $n$.

For each instruction we define the following sets:

| Set       | Meaning                                                                                      |
| --------- | -------------------------------------------------------------------------------------------- |
| `succ[i]` | The numbers of all **instructions** that may be executed **directly after** instruction `i`. |
| `gen[i]`  | The set of **variables** whose values are **read** by instruction `i`.                       |
| `kill[i]` | The set of variables that are **overwritten** by instruction `i`.                            |
| `in[i]`   | The set of variables that are **live at the start** of instruction `i`.                      |
| `out[i]`  | The set of variables that are **live at the end** of instruct `i`.                           |
In the end, what we need is `out[i]` for all instructions.

## Constructing `succ` Sets

- `succ[i] = {i + 1}` unless instruction i is `GOTO`, `IF`, or `RETURN`.	
- `succ[i] = {j}`, 
	- if instruction `i` is `GOTO x` 
	- and instruction `j` is `LABEL x`.
- `succ[i] = {j, k}`, 
	- if instruction `i` is `IF c THEN l1 ELSE l2`, 
	- instruction `j` is `LABEL l1` 
	- and instruction `k` is `LABEL l2`
- `succ[i] = ∅`, if instruction `i` is `RETURN x`.

## Constructing `gen` and `kill` Sets

Below, `k` denotes a constant, `M[...]` denotes memory access.

| Instruction `i`                | `gen[i]` | `kill[i]` | Explained                                           |
| ------------------------------ | -------- | --------- | --------------------------------------------------- |
| `LABEL l`                      | `Ø`      | `Ø`       |                                                     |
| `x := y`                       | `{y}`    | `{x}`     |                                                     |
| `x := k`                       | `Ø`      | `{x}`     |                                                     |
| `x := unop y`                  | `{y}`    | `{x}`     |                                                     |
| `x := unop k`                  | `Ø`      | `{x}`     |                                                     |
| `x := y binop z`               | `{y, z}` | `{x}`     |                                                     |
| `x := y binop k`               | `{y}`    | `{x}`     |                                                     |
| `x := M[y]`                    | `{y}`    | `{x}`     |                                                     |
| `x := M[k]`                    | `Ø`      | `{x}`     |                                                     |
| `M[x] := y`                    | `{x, y}` | `Ø`       | `x` is also used as a variable <br>to access memory |
| `M[k] := y`                    | `{y}`    | `Ø`       |                                                     |
| `GOTO l`                       | `Ø`      | `Ø`       |                                                     |
| `IF x relop y THEN lt ELSE lf` | `{x, y}` | `Ø`       |                                                     |
| `x := CALL f (args)`           | `args`   | `{x}`     | `args` are variables too                            |
| `RETURN x`                     | `{x}`    | `Ø`       |                                                     |

