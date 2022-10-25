# Harry-Potter-Dialogue-Dataset
 This repository contains resources for accessing the official training and test data of Harry Potter Dialogue Dataset (***HPD***).
## Overview
We present HPD: Harry Potter Dialogue Dataset to facilitate the study of building dialogue agents for characters in a story. It differs from existing dialogue datasets in two aspects: 1) HPD provides rich background information about the novel Harry Potter, including scene, character attributes, and character relations; 2) All these background information will change as the story goes on. In other words, each dialogue session in HPD correlates to a different background, and the storyline determines how the background changes.

Harry Potter Dialogue is the first dialogue dataset that integrates with **scene**, **attributes** and **relations** which are **dynamically** changed as the **storyline** goes on. Our work can facilitate research to construct more human-like conversational systems in practice. For example, virtual assistant, NPC in games, etc

![](task.png) 

Formally, the task of building dialogue agents for characters in a storyline can be defined as follows: Given a dialogue history $\mathbf{H}$,  corresponding dialogue scene $\mathbf{S}$ and participants information $\mathbf{P}$ as input, which are changed depending on the development of storyline, as shown in the Figure.

The dialogue agent  is supposed to generate a  response $\mathbf{Y} = y_1, y_2,...,y_n$:

$$\mathcal{Y}=argmax_Y \textit{P}(\mathbf{Y}|\mathbf{H},\mathbf{S},\mathbf{P})$$

In this repository, we release ***Chinese and English*** versions of collected ***HPD***. Notice that, due to the misalignment of English and Chinese story corpus, the  collected data in English and Chinese may slightly differ.


### Quick Links



## Datasets

Our datasets consist of the following parts:

- **Dialogue:** collected from Harry Potter Novel
- **Scene:** the text that surrounds and immediately relates to the dialogue is regarded as the scene.
- **Attributes:** We collect 13 attributes of each character in total: $\texttt{Gender}, \texttt{Age}, \texttt{Lineage}, \texttt{Talents}, \texttt{Looks} ,\texttt{Achievement}, \texttt{Title}, \texttt{Belongings}, \texttt{Export},  \texttt{Hobby}, \texttt{Character}, \texttt{Spells}, \texttt{Nickname}$
- **Relations:** We collect 12 relations of each character with Harry: $\texttt{Friend}, \texttt{Classmate}, \texttt{Teacher}, \texttt{Family}, \texttt{Lover}, \texttt{Opponent},  \texttt{Teammate}, \texttt{Enemy}$, Harry's $\texttt{Familiarity}$ to someone, Harry's $\texttt{Affection}$ to someone, someone's $\texttt{Familiarity}$ to Harry, and someone's $\texttt{Affection}$ to Harry.

Our dataset are annotated by four professional annotaters (Harry Potter Fans), which is divided into four stages:
- Four annotaters are required to read the Harry Potter book first;
- Three of them are required to annotate correponding information;
- Another one is responsible for intergrating their annotations to get high agreement data;
- Last, we manually double-check and revise mistakes to further ensure the data quality.

### Training Data

we request the annotators to extract all multi-turn dialogues from the books. Besides, the speaker name of each utterance in the session is labeled as well. As result, we collect 1042 dialogue sessions as our training set.

### Test Data

### Attributes and Relations

We divide the attributes into two categories: (1) inborn; (2) nurture. The former denotes some innate attributes or abilities, which contains $\texttt{Gender}, \texttt{Age}, \texttt{Lineage}, \texttt{Talents}, \texttt{Looks}$. The latter refers to properties through acquired efforts or opportunities, including  $\texttt{Achievement}, \texttt{Title}, \texttt{Belongings}, \texttt{Export},  \texttt{Hobby}, \texttt{Character}, \texttt{Spells} , \texttt{Nickname}$.

The relations between Harry and other characters can be classified into **binary relations** and **discrete relations**. The former includes 8 types, which are $\texttt{Friend}, \texttt{Classmate}, \texttt{Teacher}, \texttt{Family}, \texttt{Lover}, \texttt{Opponent},  \texttt{Teammate}, \texttt{Enemy}$. There are 4 types of discrete relations: (1) Harry's $\texttt{Familiarity}$ to someone, (2) Harry's $\texttt{Affection}$ to someone, (3) someone's $\texttt{Familiarity}$ to Harry, and (4) someone's $\texttt{Affection}$ to Harry. In our dataset, the familiarity ranges from 0 to 10, and the affection ranges from -10 to 10. 

### Annotation Rules


### Data Format

#### Personal-Dialogue Format

### Data Stastics

### Data Download

## Evaluation

## Baseline

## Citation
