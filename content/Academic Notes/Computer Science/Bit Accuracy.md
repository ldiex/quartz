Any scientific field needs its academic rigor by pursuing accuracy and precision. Computer science pursues *bit accuracy*: **any computational process is accurate and precise up to every bit.** 

Here bit is short for *binary digit*, the smallest digital symbol which has a value of $0$ or $1$.
Scientific experiments have requirements of accuracy and precision according to the standards and best practices of their domains. For instance, we may see expressions such as “experiments results are statistically significant when the $p$-value is less than $0.05$”, “the error is no more than $3$ Angstrom ($\mathrm{Å}$)”, and “the results are precise up to four digits after the decimal point”. **All of these are not bit accurate.**

Computer science works complementarily with these domains **by guaranteeing bit accuracy when processing experimental data, doing simulation, or conducting theoretical reasoning**

For example, in [[Golang|Go programming language]], *type accuracy* is a kind of bit accuracy: while $1$ is regarded as a `int` number, $1.0$ would be regarded as `float` number, which is different from the field of mathematics.

Scientific progress can be made without mathematical exactness or bit accuracy.
Sometimes it is meaningful just to establish that factor A is positively (or negatively)
related to factor B, when investigating a phenomenon involving factors A and B. 

Let us consider an example in psychology. The domain problem has to do with domestic violence: why does a spouse being battered not leave an abusive relationship but stay committed to marriage? Professor Caryl Rusbult proposed a theory of investment model for close relationship:
$$
\mathrm{Commitment} \propto (\mathrm{Satisfaction} \times \mathrm{Investment}) / \mathrm{Alternative}
$$
which can partially answer this question. A spouse's commitment to marriage is positively related to satisfaction and investment, but negatively related to alternatives. A battered spouse stays in an abusive relationship, not due to marriage satisfaction, but because she/he has invested heavily (e.g., having children) or has poor alternatives (e.g., without independent income). **Rusbult's investment model is not mathematically exact or bit accurate, but it is indeed a scientific progress, an inspirational theory which can lead to social policies and guides for individual actions.** 

Computing and mathematics can be used to help test whether real data show that commitment is related positively to satisfaction and investment, but negatively to alternatives. Doman scientists, such as psychologists, utilize their professional expertise and
domain knowledge to advance their fields and contribute to society. Computer scientists complement their efforts by offering mental tools and computing hardware and software that feature [[Automatically Execution|automatically executed]], bit-accurate, constructive abstractions of information transformation.