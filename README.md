# Harry-Potter-Dialogue-Dataset
 This repository contains resources for accessing the official training and test data of Harry Potter Dialogue Dataset (***HPD***).
## Overview
We present HPD: Harry Potter Dialogue Dataset to facilitate the study of building dialogue agents for characters in a story. It differs from existing dialogue datasets in two aspects: 1) HPD provides rich background information about the novel Harry Potter, including scene, character attributes, and character relations; 2) All these background information will change as the story goes on. In other words, each dialogue session in HPD correlates to a different background, and the storyline determines how the background changes.

![](task_definition.pdf) 

Formally, the task of building dialogue agents for characters in a storyline can be defined as follows: Given a dialogue history $\mathbf{H}$,  corresponding dialogue scene $\mathbf{S}$ and participants information $\mathbf{P}$ as input, which are changed depending on the development of storyline.

The dialogue agent  is supposed to generate a  response $\mathbf{Y} = y_1, y_2,...,y_n$:

$$\mathcal{Y}=argmax_Y \textit{P}(\mathbf{Y}|\mathbf{H},\mathbf{S},\mathbf{P})$$

In this repository, we release ***Chinese and English*** versions of collected ***HPD***. Notice that, due to the misalignment of English and Chinese story corpus, the  collected data in English and Chinese may slightly differ.


### Quick Links



## Datasets


### Training Data

### Test Data

### Attributes and Relations

### Data Format

#### Personal-Dialogue Format

### Data Stastics

### Data Download

## Evaluation

## Baseline

## Citation
