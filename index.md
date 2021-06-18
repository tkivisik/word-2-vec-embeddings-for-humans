## Seeking Human Bias With Word Embeddings

June 2021, Taavi Kivisik

### Introduction

There is a growing frustration with the lack of abstraction and generalization of artificial neural networks (ANN). While performance in computer vision tasks keeps improving, the improvement does not come from models understanding what is on the image (Jo and Bengio, 2017), but rather from more efficient use of surface level statistical regularities. Adversarial examples where changing a few pixels makes the model predict a wrong class with high confidence (e.g. Szegedy et al., 2014) is a great example of the lack of understanding in artificial intelligence (AI) models.

This lack of abstraction and generalization is in stark contrast with what humans are capable of. Humans demonstrate abstract thinking and pattern recognition by solving math problems, writing poetry, composing music, as well as by understanding analogies and metaphors. These skills rely on combining relevant ideas together in novel but plausible ways. This plausibility can also be thought of as a sense of compatibility with the rest of the patterns we have recognized about the world.

Humans seem to be so tuned for patterns that we can not seem to stop even when we want to. This is true on a perceptual level (e.g. we can not stop seeing the squares A and B as being of different color on Figure \ref{fig:checker-illusion}) as well as on a cognitive level (e.g. a literature review by Furnham and Boo (2011) of the anchoring effect reveals that even expertise does not eliminate the effect of anchoring). Humans are also bad at generating random numbers, saying the same digit twice in a row 7.57% of the time (10% expected for a fully random sample) and having the next digit one higher than the previous one 15.44% of the time (9% expected for a fully random sample (Figurska et al., 2008).

FIGURE 1 checker illusion

In this study I propose to see human bias as a feature at least from the generalization perspective, and use it to explore word embeddings. More precisely, I analyze data where human participants were asked to come up with 10 words semantically as far apart from each other as possible. This project contributes to the debate about the abstraction and generalization in ANNs by studying whether human bias can be detected using word embeddings in order to pave the way for AI systems inspired by the only known great generalizers, humans.

I propose to test an alternative hypothesis stating that when humans are asked to say words that are semantically as far apart as possible, then these words will be closer together in a word embedding space than any random two words.

### Method

#### Data

Data used in this project was originally collected for a study by Uibopuu and Aru with colleagues (2021). They asked participants to write down 10 words in Estonian that are semantically as far apart from each other as possible. Hele-Andra Kuulmets exported these data in a tabular format and developed a basic distance metric.

After removing pilot participants, there were a total of 139 unique users participating in a total of 728 sessions. They used a total of 7085 words in complete sessions (where none of the 10 words was unknown), and 2216 of them were unique.

#### Word embeddings

I used pretrained 100 dimensional word embeddings from Eesti Keeleressursside Keskus (https://entu.keeleressursid.ee/shared/7540/I7G5aC1YgdInohMJjUhi1d5e4jLdhQerZ4ikezz1JEv3B9yuJt9KiPl9lrS87Yz0). Embeddings trained on whole words were used instead of lemmas as the former led to a lesser loss in creativity data (less unknown words). Skip-gram (sg) as a word2vec algorithm was used instead of continuous bag-of-words (cbow) as the former handles rare words better.

#### Approach

Looking into human word sequences I get a sample of words that are considered distant by humans. An example sequence could have been "police, cardboard, bile, moto, lottery, photo, mug, bass, mass, balcony" (in Estonian). This allows me to construct two word pair conditions:
* Human pairs - where the two words were said consequently by a human (e.g. police, cardboard)
* Random pairs - where the two words are chosen at random from a pool of all words used by humans in this study (e.g. police, bile; police and some word from another sequence)

I then compare metrics like an average Euclidean distance and cosine similarity between these two words. The alternative hypothesis is that
* humans jump shorter distances between consecutive words compared to random words combined by a computer.

### Results

Welch t-test comparing the Euclidean distance between human pairs and random pairs conditions was performed (n=6180, t=-1.9970, p=0.0467). With the significance level α=0.05, we can reject the null hypothesis and claim there is a statistically significant difference between Euclidean distances of human word pairs and random word pairs. As the Welch t-test was performed two-tailed despite the directional expectation, confidence in the alternative hypothesis is even stronger.

The same two-tailed Welch t-test comparing the two human pairs and random pairs conditions was performed using cosine similarity (n=6180, t=2.2188, p=0.0265). With the significance level α=0.05, we can reject the null hypothesis once again. Therefore, we can proceed with the alternative hypothesis that there is a statistically significant difference in cosine similarity between human word pairs and random word pairs. As the t-value is positive, the human pairs has a higher average cosine similarity.

### Discussion



### Contribution

Data was collected by Oliver Uibopuu, basic transformation into a table by Hele-Andra Kuulmets. My contribution was literature overview, data preprocessing, analysis, and writing up the blog.




```markdown
![Image](src)
```
