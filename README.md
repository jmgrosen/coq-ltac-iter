# coq-with-hint-db
This is a Coq plugin that provides a tactic that iterates over a hint database and passes each lemma to a given function. For example,

```
Create HintDb my_lemmas.

Hint Resolve lem1 lem2 : my_lemmas.

Ltac the_tactic :=
  let k lem := idtac lem ; fail in
  foreach [ my_lemmas ] run k.
(* OUTPUT:
lem1
lem2
*)
```
different "branches" are combined using Ltac's || operator.
