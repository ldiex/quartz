# Rules of Inference

| Tautology                                          | Name                   |
| -------------------------------------------------- | ---------------------- |
| $(p \land (p \to q)) \to q$                        | Modus ponens           |
| $(\neg q \land (p \to q) \to \neg p)$              | Modus tollens          |
| $((p \to q) \land (q \to r)) \to(p \to r)$         | Hypothetical syllogism |
| $((p \lor q) \land \neg p) \to q$                  | Disjunctive syllogism  |
| $p \to(p \lor q)$                                  | Addition               |
| $(p \lor q) \to p$                                 | Simplification         |
| $((p) \land (q)) \to(p \land q)$                   | Conjunction            |
| $((p \lor q) \land (\neg p \lor r)) \to(q \lor r)$ | Resolution             |
|                                                    |                        |
# Resolution
Computer programs have been developed to automate the task of reasoning and proving theorems. Many of these programs make use of a rule of inference known as *resolution*. (This has something to do with [[Boolean Logic#Normal forms|normal forms]])
$$
((p \lor q) \land (\neg p \lor r)) \to(q \lor r)
$$
The final disjunction is called the *resolvent*. 

