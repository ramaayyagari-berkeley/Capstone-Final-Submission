### Using Natural Language Inference to eliminate reduncency by identifing whether one text sentence can be inferrred from another text sentence symantically 

**Rama Viswanatha G Ayyagari**

#### Executive summary

**Project overview and goals:** The goal of this project is find best solution and word embeddings, given two text sentences `premises` and `hypotheses`, whether one text sentence can be inferred from another symantically by comparing pretrained `GloVe` and `BERT()` embeddings with `MLP(Multi Layer Perceptrons)` model.

**Findings:**

**Results and conclusion:**


#### Rationale
This is central topic for understanding natural language.it has wide applications ranging from information retrieval to open-domain question answering.

#### Research Question
When presented with two text sequences, `premises` and `hypotheses`, the expected result, either one of `entailment`, `contradiction` or `neutral` based on logical semantic relation between the `premises` and `hypotheses`.

##### Entailment: the hypothesis can be inferred from the premise.
    Premise: Two women hugging each other.
    Hypothesis: Two women are showing affection.
##### Contradiction: the negation of hypothesis can be inferred from premise.
    Premise: A man is running code example
    Hypothesis: The man is sleeping
##### Neutral: all other cases
    Premise: The musicians are performing for us.
    Hypothesis: The musicians are famous.

#### Data Sources
The Stanford Natural Language Inference (SNLI) Dataset has 500000 labeled English sentences pairs. URL: 'https://nlp.stanford.edu/projects/snli/snli_1.0.zip'

#### Methodology
What methods are you using to answer the question?

#### Results
What did your research find?

#### Next steps
1.
2.

#### Outline of project

- [Natural Language Inference](nli.ipynb)
- [Utility functions library](utilities.ipynb)
- [Detailed Solution](SOLUTION.md)
- [Multi Layer Perceptrons](MLP.md)
- [GloVe Embeddings](GLOVE.md)
- [BERT Embeddings](BERT.md)
- [Installation](INSTALLATION.md)


##### Contact and Further Information

Rama Viswanatha G Ayyagari

Email: gouri.ayyagari@gmail.com 

[LinkedIn](https://www.linkedin.com/in/ramaayyagari/)