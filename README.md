# Quick start

## Download data 

Download utterance, response, dict ,embedding from https://1drv.ms/u/s!AtcxwlQuQjw1jGn5kPzsH03lnG6U  , then unzip it under data path



## Running

```
cd tensorflow_src
python SCN.py
```
## Data format

1. utterances.pkl
A pair like [history, true_response], where history[i] is the history of [u1, u2, u3,...,un] for the ture response ture_response[i]

2. responses.pkl

A list of utterances, used for candidate responses.


## Results:
epoch = 7
R2: 0.72988
R1: 0.92514
loss: 0.22563

Test on Tensorflow 1.13, python 3


# Motivation

1. Learning to ingore and focus on some parts that some users may be not interested in.

2. Make the code easy to use


The source code comes from origin [rep](https://github.com/MarkWuNLP/MultiTurnResponseSelection)

# Douban Conversation Corpus

## Data set
We release Douban Conversation Corpus, comprising a training data set, a development set and a test set for retrieval based chatbot. The statistics of Douban Conversation Corpus are shown in the following table. 

|      |Train|Val| Test         | 
| ------------- |:-------------:|:-------------:|:-------------:|
| session-response pairs  | 1m|50k| 10k |
| Avg. positive response per session     | 1|1| 1.18    | 
| Fless Kappa | N\A|N\A|0.41      | 
| Min turn per session | 3|3| 3      | 
| Max ture per session | 98|91|45    | 
| Average turn per session | 6.69|6.75|5.95    | 
| Average Word per utterance | 18.56|18.50|20.74   | 


The test data contains 1000 dialogue context, and for each context we create 10 responses as candidates. We recruited three labelers to judge if a candidate is a proper response to the session. A proper response means the response can naturally reply to the message given the context. Each pair received three labels and the majority of the labels was taken as the final decision.

<br>
As far as we known, this is the first human-labeled test set for retrieval-based chatbots. 
Location：https://www.dropbox.com/s/90t0qtji9ow20ca/DoubanConversaionCorpus.zip?dl=0


## Data template
label \t conversation utterances (splited by \t) \t response


## Source Code
We also release our source code to help others reproduce our result. The code has been tested under Ubuntu 14.04 with python 2.7. 

Please first run preprocess.py and edit the code with the correct path, and it will give you a .bin file. After that, please run SMN_Last.py with the generated .bin file, and the training loss will be printed on the screen. If you set the train_flag = False, it will give your predicted score with your model. 

Some tips:

The 200-d word embedding is shared at https://1drv.ms/u/s!AtcxwlQuQjw1jF0bjeaKHEUNwitA . The shared file is a list has 3 elements, one of which is a word2vec file. Please Download it and replace the input path (Training data) in my scripy. 

Tensorflow resources:

The tensorflow code requires several data set, which has been uploaded on the following path:

Resource file: https://1drv.ms/u/s!AtcxwlQuQjw1jGn5kPzsH03lnG6U 

Worddict file: https://1drv.ms/u/s!AtcxwlQuQjw1jGrCjg8liK1wE-N9

Requirement: tensorflow>=1.3


## Reference
Please cite our paper if you use the data or code in this repos.

Wu, Yu, et al. "Sequential Matching Network: A New Archtechture for Multi-turn Response Selection in Retrieval-based Chatbots." ACL. 2017.
