# Definition
The problem focuses on the relation between the [[Complexity Classes|complexity classes]] P and NP, where the class P consists of all [[Decision Problem|decision problems]] solvable on a deterministic sequential machine in a duration polynomial in the size of the input; and the class NP consists of all decision problems whose positive solutions are verifiable in polynomial time given the right information.

Clearly, P $\subset$ NP, but the biggest open question in theoretical computer science concerns whether P $=$ NP ?

# NP-completeness
To attack the P $=$ NP question, the concept of *NP-completeness* is very useful. *NP-complete problems* are problems that any other NP problem is *reducible* to in polynomial time and whose solution is still verifiable in polynomial time （so NP-complete problems are also NP problems）. That is, **any NP problem can be transformed into any NP-complete problem**. Informally, an NP-complete problem is an NP problem that is at least as "tough" as any other problem in NP.

NP-hard problems are those at least as hard as NP problems; i.e., all NP problems can be reduced (in polynomial time) to them. **NP-hard problems need not be in NP**; i.e., they need not have solutions verifiable in polynomial time.

## Examples of NPC Problems
From the definition alone it is unintuitive that NP-complete problems exist; however, a trivial NP-complete problem can be formulated as follows: 

> Given a [[Turing Machine|Turing machine]] $M$ guaranteed to halt in polynomial time, does a polynomial-size input that $M$ will *accept* exist?

It is in NP because (given an input) it is simple to check whether $M$ accepts the input by simulating $M$; it is NP-complete because the verifier for any particular instance of a problem in NP can be encoded as a polynomial-time machine $M$ that takes the solution to be verified as input. Then the question of whether the instance is a yes or no instance is determined by whether a valid input exists.

Another famous NP-complete problem is [[Boolean Satisfiability Problem (SAT)|Boolean satisfiability problem]], or *SAT*
