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

HPD constructs a test set with 178 dialogue sessions to evaluate how similar a dialogue system is to Harry Potter. Each session in our test set consists of at least one positive response and 9 negative responses. This test set can facilitate the evaluation of both generation-based and retrieval-based dialogue systems.

### Attributes and Relations

We divide the attributes into two categories: (1) inborn; (2) nurture. The former denotes some innate attributes or abilities, which contains $\texttt{Gender}, \texttt{Age}, \texttt{Lineage}, \texttt{Talents}, \texttt{Looks}$. The latter refers to properties through acquired efforts or opportunities, including  $\texttt{Achievement}, \texttt{Title}, \texttt{Belongings}, \texttt{Export},  \texttt{Hobby}, \texttt{Character}, \texttt{Spells} , \texttt{Nickname}$.

The relations between Harry and other characters can be classified into **binary relations** and **discrete relations**. The former includes 8 types, which are $\texttt{Friend}, \texttt{Classmate}, \texttt{Teacher}, \texttt{Family}, \texttt{Lover}, \texttt{Opponent},  \texttt{Teammate}, \texttt{Enemy}$. There are 4 types of discrete relations: (1) Harry's $\texttt{Familiarity}$ to someone, (2) Harry's $\texttt{Affection}$ to someone, (3) someone's $\texttt{Familiarity}$ to Harry, and (4) someone's $\texttt{Affection}$ to Harry. In our dataset, the familiarity ranges from 0 to 10, and the affection ranges from -10 to 10. 

### Annotation Rules

- **Affection:** is rated on a twenty-level, ranging from -10 to 10, where 10 indicates the highest affection and -10 indicates the lowest affection. And
$\texttt{Score(Affection)>0}$ denotes the character has the positive relationship  with Harry while $\texttt{Score(Affection)<0}$ means the character has the negative relationship  with Harry.

- **Familiarity:**  we also rate $\texttt{Familiarity}$ with 10 level, which ranges from 0 to 10, where 10 indicates the highest affection and 0 indicates the lowest affection. Concretely, $\texttt{Score(Familiarity)=0}$ denotes stranger, and $\texttt{Score(Familiarity)=10}$ denotes two characters who are often stay together and very familiar with each other's habits, secrets and temperaments.

Detailed annotation steps and rules can be seen in our paper.

### Data Format
We process our data in a unified format, and store in json files. The general format is:

```

{
"dialogue-xx":{
  "Position": <Chapter-Scene>,
  "Speakers": [speaker-1, ..., speaker-n],
  "Scene": <context>,
  "Dialogue": <dialogue context>,
  "Positive-Response": <response text>,
  "Negative- Response": [<negative_text_1>, ..., <negative_text_n>] (test set only)
  "Attributes": {
    "speaker-1": {
      "name": <name_text>,
      "nickname": <nickname_text>,
      ...
      "Spells": <spells_text>
    },
    ...
    "speaker-n": {
      "name": <name_text>,
      "nickname": <nickname_text>,
      ...
      "Spells": <spells_text>
    }
    
  }
  "Relations With Harry": {
  "speaker-1": {
      "name": <name_text>,
      "friend": <friend_score>,
      ...
      "His familiarity with Harry": <familiarity_score>
    },
    ...
    "speaker-n": {
      "name": <name_text>,
      "friend": <friend_score>,
      ...
      "His familiarity with Harry": <familiarity_score>
    }
  }
    }
```
#### Fields

- **dialogue-xx** Denotes the index of the dialogue in our dataset.
- **Position:** Denotes the timeline of the dialogue in the novel. "ChapterX-Y" refers to the dialogue occurs in the Y-th scene of X-th Chapter in the book.
- **Speakers:** Participants in the dualogue.
- **Scene:** Context of the dialogue.
- **Dialogue:** Dialogue history.
- **Positive-Response:** Human annotated response.
- **Negative-Response:** Negative responses generated by large pre-trained language models.
- **Attributes:** Character attributes.
- **Relations:** Character Relations With Harry.

Also, we can free to change our dataset into other formats, such as ***Personal-Dialogue Format***.

### Data Stastics


| Train | Chinese|English| Test | Chinese|English|
| :----- | :-------------------:| :------------------: |:----- | :-------------------:| :------------------: |
| Average Turns | 13.8  | 14.25  |Average Turns | 8.6 | 6.58 |
| Maximum Speakers| 20  | 20 |Maximum Speakers| 8 | 8 |
| Minimum Speakers | 2  | 2  |Minimum Speakers | 2 | 2 |
| Average Utterance Length | 32.9 | 17.4 |Average Utterance Length | 28.3| 17.42 |
| Maximum Utterance Length | 77 | 68 |Maximum Utterance Length | 31 | 28 |
| Minimum Utterance Length | 3 | 1 |Minimum Utterance Length | 7 | 1 |
| Total Dialogues | 1042 | 1110 |Total Dialogues | 178 | 165 |



### Data Download

## Evaluation

## Baseline

## Citation
