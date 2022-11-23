# Harry-Potter-Dialogue-Dataset
 This repository contains resources for accessing the official training and test data of Harry Potter Dialogue Dataset (***HPD***). The HPD is proposed in the paper: [**What would Harry say? Building Dialogue Agents for Characters in a Story**](https://arxiv.org/abs/2211.06869)
 
**************************** **Updates** ****************************

- 22/11/2022: We provide a new [executable file](https://drive.google.com/file/d/1rDQs0O8CGrqBKHaJGYzwJiky23FzXuAZ/view?usp=share_link) to download all collected data in HPD. See [ALL_DATA Download](#all_data-download) for more details.
 
 
## Overview
We present HPD: Harry Potter Dialogue Dataset to facilitate the study of building dialogue agents for characters in a story. It differs from existing dialogue datasets in two aspects: 1) HPD provides rich background information about the novel Harry Potter, including scene, character attributes, and character relations; 2) All these background information will change as the story goes on. In other words, each dialogue session in HPD correlates to a different background, and the storyline determines how the background changes.

Harry Potter Dialogue is the first dialogue dataset that integrates with **scene**, **attributes** and **relations** which are **dynamically** changed as the **storyline** goes on. Our work can facilitate research to construct more human-like conversational systems in practice. For example, virtual assistant, NPC in games, etc. Moreover, HPD can both support dialogue **generation** and **retrieval** tasks.

![](task.png) 

Formally, the task of building dialogue agents for characters in a storyline can be defined as follows: Given a dialogue history $\mathbf{H}$,  corresponding dialogue scene $\mathbf{S}$ and participants information $\mathbf{P}$ as input, which are changed depending on the development of storyline, as shown in the Figure.

The dialogue agent  is supposed to generate a  response $\mathbf{Y} = y_1, y_2,...,y_n$:

$$\mathcal{Y}=argmax_Y \textit{P}(\mathbf{Y}|\mathbf{H},\mathbf{S},\mathbf{P})$$

In this repository, we release ***Chinese and English*** versions of collected ***HPD***. Notice that, due to the misalignment of English and Chinese story corpus, the  collected data in English and Chinese may slightly differ.

### Quick Links

- [Datasets](#datasets)
 - [Training Data](#training-data)
 - [Attributes and Relations](#attributes-and-relations)
 - [Data Format](#data-format)
 - [Data Stastics](#data-stastics)
 - [Data Download](#data-download)
   - [Attributes and Relations Download](#attributes-and-relations-download)
   - [Json-File Download](#json-file-download)
   - [ALL_DATA Download](#all_data-download)
- [Baseline Evaluation and Download](#baseline-evaluation-and-download)
- [Citation](#citation)




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

Considering not all characters are essential to understanding and driving the story in Harry Potter series, we choose ***113 important characters*** to annotate their attributes and relations, such as Harry, Ron and etc.

### Training Data

we request the annotators to extract all multi-turn dialogues from the books. Besides, the speaker name of each utterance in the session is labeled as well. As a result, we collect 1042 dialogue sessions as our training set.

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



### Data Stastics


| Train | Chinese|English| Test | Chinese|English|
| :----- | :-------------------:| :------------------: |:----- | :-------------------:| :------------------: |
| Average Turns | 13.8  | 14.25  |Average Turns | 8.6 | 6.58 |
| Maximum Speakers| 20  | 20 |Maximum Speakers| 8 | 8 |
| Minimum Speakers | 2  | 2  |Minimum Speakers | 2 | 2 |
| Average Utterance Length | 32.9 | 17.4 |Average Utterance Length | 28.3| 17.42 |
| Maximum Utterance Length | 77 | 68 |Maximum Utterance Length | 31 | 28 |
| Minimum Utterance Length | 3 | 1 |Minimum Utterance Length | 7 | 1 |
| Total Dialogues | 1042 | 1097 |Total Dialogues | 178 | 165 |



### Data Download
#### Ethical Statement
To avoid the potential issue of using Harry Potter Novels, we promise the annotated dataset is developed for non-commercial use. Moreover, we only provide the line number and page number of each collected dialogue in Harry Potter novel rather than give the detailed content of each dialogue session.  We further supply the script to extract corresponding raw dialogue data from the novels according to the provided line and page numbers. As for the annotated character attributes and relations, we have our own copyright and  release for research communities.

#### Download

#### Attributes and Relations Download
We annotate our character and relations of 113 characters chapter by chapter, and store these fine-grained annotated data in ***excel*** files.

**Chinese** version of annotated character and relations can be download here: [Attributes](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/Emq8snnAuSxBqmwfmwGc8O4Bfz76qAkqmxP_qoS_WLKx-g?e=I51mYV) and [Relations](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EimqQU125LlBocVdkyqYUa0BmiX5vF7Q-UnHiY_dA7L-Lw?e=MbWqqh)

**English** version of annotated character and relations can be download here: [Attributes](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EiUBB4ee6jdJnrvkW5zVjMgB1ylG9QDVTuvItibpFmDtbg?e=rFrG5E) and [Relations](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EoP66AgnW6ZJjACBbMF389cBI4-DEWKeadu2oEphma0xZQ?e=IyzdFO)

#### Json-File Download
To be convenient for each researcher, we provide a executable file (.exe) to directly extract the line number and page number of each collected dialogue in Harry Potter novel with annotated attributes and relations into json-files.

you can download the executable file from : [English](https://drive.google.com/file/d/1cuoYGpEcux81gHXmmtm2RmZuyHpGCULm/view?usp=share_link) and [Chinese](https://drive.google.com/file/d/1cJkkY9NvfCLFW1TSdfJTzvMbgIVyNhct/view?usp=share_link).

Notice that, the executable file runs the transcript to process the data in our server. Hence, you may need your vpn opened if you are in China Mainland.
If you have any issuse with getting json files, please drop the email to chennuo26@gmail.com.
#### Data Format
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

- **dialogue-xx:** Denotes the index of the dialogue in our dataset.
- **Position:** Denotes the timeline of the dialogue in the novel. "ChapterX-Y" refers to the dialogue occurs in the Y-th scene of X-th Chapter in the book.
- **Speakers:** Participants in the dualogue.
- **Scene:** Context of the dialogue.
- **Dialogue:** Dialogue history.
- **Positive-Response:** Human annotated response.
- **Negative-Response:** Negative responses generated by large pre-trained language models.
- **Attributes:** Character attributes.
- **Relations:** Character Relations With Harry.

Also, we can free to change our dataset into other formats, such as ***Personal-Dialogue Format***. Notice that, sometimes "Relations With Harry" could be none if the dialogue speakers not in the annotated 113 important characters.

### All_Data Download

Morever, we provide another [executable file](https://drive.google.com/file/d/1rDQs0O8CGrqBKHaJGYzwJiky23FzXuAZ/view?usp=share_link) (.exe) to download:

- All json-format files for training/evaluating.
- All annotated attributes and relations of 113 important characters stored in excel-format files.
- Raw novel corpus in Chinese and English. You can utilize them to pre-train your dialogue or text generative models (like GPT-2 in the paper), as well as post-train dialogue retrieval models.




## Baseline Evaluation and Download

Here we report automatic and huaman evaluations results of four baselines in our paper (only Chinese at the time).
### Automatic Evaluation
#### Generative Models
|Model |  $\textbf{Dist.1}(\uparrow)$| $\textbf{PPL}(\downarrow)$ | $\Delta\textbf{P}(\uparrow)$ | $\textbf{MAuVE}(\uparrow)$ | ${\Delta \textbf{M}}(\uparrow)$  |
| :----- | :-------------------:| :------------------: |:------------------: |:------------------: |:------------------: |
| GPT-2 | 9.86  | 18.3 | 0.12| 0.809 | -0.164 |
| Ori-BOB | 12.87|  3.03| 0.21| 0.940|-0.011 | 
| [Per-BOB](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EtsoTZX_FiROurpSeMMvz58Baf8WRMMSms0KH6Tr6Kew_w?e=JwmHVB) | 13.25 |  2.41| 0.08|0.948| 0.003 |
|  [EVA](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/Er9KPQnj5TZHk4K5nCZYRCkBRSJ9idwMJwf41T0raZs3FQ?e=0bV0gb)    | 23.01    | 37.8 | 0.54|0.968| 0.192 |


The definitions of  $\Delta\textbf{P}(\uparrow)$ and ${\Delta \textbf{M}}(\uparrow)$ please refer to our paper (Section 5.2).

#### Retrieval-based Models

|Model |  $\textbf{MAR}(\uparrow)$| $\textbf{MRR}(\uparrow)$ | $\textbf{P@1}(\uparrow)$ | $\textbf{R10@1}(\uparrow)$  | $\textbf{R10@5}(\uparrow)$   |
| :----- | :-------------------:| :------------------: |:------------------: |:------------------: |:------------------: |
|  [BERT-FP](https://drive.google.com/file/d/1fTrIh0LQ2NGtC0SS12k8dOz5WE40tzbG/view) | 0.468  | 0.468 | 0.259 | 0.259 | 0.788 |


#### Human Evaluation
|Model |  $\textbf{Fluency}$ | $\textbf{Relevance with the Scene}$ | $\textbf{Relevance with the  Attributes}$ | $\textbf{Relevance with the Relations}$  |
| :----- | :-------------------:| :------------------: |:------------------: |:------------------: |
| GPT-2 | 3.34  |1.68   | 1.9 | 1.5 |
| [EVA](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/Er9KPQnj5TZHk4K5nCZYRCkBRSJ9idwMJwf41T0raZs3FQ?e=0bV0gb) |  $\textbf{4.27}$ | $\textbf{2.38}$  | $\textbf{2.5}$ | 2.04 | 
| Ori-BOB | 4.01  | 1.93 |  1.78 |1.9 |
| [Per-BOB](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EtsoTZX_FiROurpSeMMvz58Baf8WRMMSms0KH6Tr6Kew_w?e=JwmHVB)  |4.2  | 2.01 |  2.16 | $\textbf{2.15}$ |


Note: 
- We initialize GPT-2 model from the checkpoint which pre-trained in the Tencent business data (the general results are much better than open-source GPT-2), hence we don't public the source of our GPT-2 here.
- We initialize our BOB models from [here](https://hkustgz-my.sharepoint.com/:f:/g/personal/nchen022_connect_hkust-gz_edu_cn/EiNa1Hd844BPjrifPzmQMH0By_OppTRQ4nO9uBQR2aQo7Q?e=pQ4qTu). The training scripts of BOB please refer to its originial  [project](https://github.com/songhaoyu/BoB).
- The training scripts of EVA please refer to its originial  [project](https://github.com/thu-coai/EVA).
- We post-train BERT-FP models in [Douban corpus](https://github.com/hanjanghoon/BERT_FP) and then fine-tune in HPD dataset to get better performance.


## Citation
```
  @article{chen2022would,
  title={What would Harry say? Building Dialogue Agents for Characters in a Story},
  author={Chen, Nuo and Wang, Yan and Jiang, Haiyun and Cai, Deng and Chen, Ziyang and Li, Jia},
  journal={arXiv preprint arXiv:2211.06869},
  year={2022}
}
```
