### Natural Language Inference using Attention and MLPs (Multi Layer Perceptrons)

#### Methodology
The Natural Language Inference with attention methodology (with multi layer perceptrons, MLPs) know as `Decomposable Attention Model`. The solution will feeds pre-trained `GloVe` word embeddings to the architecture based on attention and MLPs(Multi Layer Perceptrons).

![NLI.Attention](images/readme/NLI.GloVe.png)

##### Model

We align tokens in one text sequence to every token on the other, and vice-versa, then compare and aggregate such information to predict the logical relationship between text sequences, `premises` and `hypotheses`.

![Decomposaable Attention Model](images/readme/NLI.Attention.Solution.png)

At a highlevel, it consists of three jointly trained steps: attending, comparing, and aggregating.

##### Attending

First step is to align tokens in one text sequence to each other in the other text sequence. Suppose the premise is `i do need slpeep` and the hypothesis is `i am tired`.Due to semantic similarlity, we may wish to align `i` in the hypothesis with `i` in premise, and align `tired` in the hypohesis with `sleep` in the premise. Likewise we may wish to align `i` in the premise with `i` in the hypohesis and align `need ` and `sleep` in the premise with the `tired` in the hypohesis. This is `soft` alignment using weighted average, where ideally large weights are associated with the tokens to be aligned, as outlined below. This is 'hard` way.

Let A = (a<sub>1</sub>, ....., a<sub>m</sub>) and B = (b<sub>1</sub>, ...., b<sub>n</sub>) the premsie and hyphothesis, where number of tokens are m and n respectively, where a<sub>i</sub>, b<sub>j</sub> ∈ R<sup>d</sup> (i = 1, ..., m, j = 1, ..., n) is a `d`-dimentional word vector. for `soft` alignment, we compute the attention weights e<sub>ij</sub> ∈ R as e<sub>ij</sub> = f(<sup>(a<sub>i</sub>)T</sup>) f(b<sub>j</sub>) where the function f is an MLP (multilayer perceptron).𝑓 takes inputs a<sub>𝑖</sub> and b<sub>𝑗</sub> separately rather than takes a pair of them together as input.This `decomposition` trick leads to only 𝑚+𝑛 applications (linear complexity) of 𝑓 rather than 𝑚𝑛 applications (quadratic complexity).

To mormalize the attention weights, we compare the weighted average of all the token vectors in the hypohesis to obtain representation of the hypothesis that is softly aligned with the token indexed by `i` in the premise:
    
$$ 𝜷_i = \sum_{j=1}^n  ( exp(e_ij) / \sum_{k=1}^n exp(e_ik) ) b_j $$

Likewise, we compute soft alignment of premise tokens for each token indexed by 𝑗 in the hypothesis

$$ 𝜶_j = \sum_{i=1}^m  ( exp(e_ij) / \sum_{k=1}^m exp(e_kj) ) a_i $$

##### Comparing

In the next step, we compare a token in one sequence with the other sequence that is softly aligned with that token. Note that in soft alignment, all the tokens from one sequence, though with probably different attention weights, will be compared with a token in the other sequence.For example, suppose that the attending step determines that `need` and `sleep` in the premise are both aligned with `tired` in the hypothesis, the pair `tired–need sleep` will be compared.

In the comparing step, we feed the concatenation (operator [.,.]) of tokens from one sequence and aligned tokens from the other sequence into a function 𝑔 (an MLP):

$$ V_A,i = g([a_i,𝜷_i]), i = 1, ......, m $$
$$ V_B,j = g([b_j,𝜶_j]), j = 1, ......, n $$

v𝐴,𝑖 is the comparison between token 𝑖 in the premise and all the hypothesis tokens that are softly aligned with token 𝑖; while v𝐵, 𝑗 is the comparison between token 𝑗 in the hypothesis and all the premise tokens that are softly aligned with token 𝑗.

##### Aggregating

With two sets of comparison vectors v𝐴,𝑖 (𝑖 = 1, . . . , 𝑚) and v𝐵, 𝑗 ( 𝑗 = 1, . . . , 𝑛) on hand, in the last step we will aggregate such information to infer the logical relationship. We begin by summing up both sets:

$$ V_A = \sum_{i=1}^m V_A,i $$

$$ V_B = \sum_{j=1}^n V_B,j $$

Next we feed the concatenation of both summarization results into function ℎ (an MLP) to obtain the classification result of the logical relationship:

$$ \hat{y} = h([V_A,V_B]) $$
