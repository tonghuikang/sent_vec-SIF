# My notes

I have yet to get anything out of it. I expected to obtain a vector from embedding, but there are issues.
https://github.com/tonghuikang/SIF/blob/master/src/SIF_embedding.py died while running :( 
Currently I am increasing the RAM

840B glove uses 64% of GCP 8vCPU 52GB ram

need to use python2 it seems to use code from data_io.py referenced in  SIF_embedding.py 
ValueError: could not convert string to float: '.'

Why you no try running your code :(
NameError: global name 'seq1' is not defined
https://github.com/PrincetonML/SIF/issues/25

Also the code got problem :(
https://github.com/PrincetonML/SIF/issues/26

Overloading of "params"
So I changed some "params" to "paramsz"

Works now, committing soon. I don't know how the vectors work though, need to read the code and or paper :/

# SIF

This is the code for [the paper](https://openreview.net/forum?id=SyK00v5xx) "A Simple but Tough-to-Beat Baseline for Sentence Embeddings".

The code is written in python and requires numpy, scipy, pickle, sklearn, theano and the lasagne library. 
Some functions/classes are based on the [code](https://github.com/jwieting/iclr2016) of John Wieting for the paper "Towards Universal Paraphrastic Sentence Embeddings" (Thanks John!). The example data sets are also preprocessed using the code there.

## Install
To install all dependencies `virtualenv` is suggested:

```
$ virtualenv .env
$ . .env/bin/activate
$ pip install -r requirements.txt 
```

## Get started
To get started, cd into the directory examples/ and run demo.sh. It downloads the pretrained GloVe word embeddings, and then runs the scripts: 
* sif_embedding.py is an demo on how to generate sentence embedding using the SIF weighting scheme,
* sim_sif.py and sim_tfidf.py are for the textual similarity tasks in the paper,
* supervised_sif_proj.sh is for the supervised tasks in the paper.

Check these files to see the options.

## Source code
The code is separated into the following parts:
* SIF embedding: involves SIF_embedding.py. The SIF weighting scheme is very simple and is implmented in a few lines.
* textual similarity tasks: involves data_io.py, eval.py, and sim_algo.py. data_io provides the code for reading the data, eval is for evaluating the performance, and sim_algo provides the code for our sentence embedding algorithm.
* supervised tasks: involves data_io.py, eval.py, train.py, proj_model_sim.py, and proj_model_sentiment.py. train provides the entry for training the models (proj_model_sim is for the similarity and entailment tasks, and proj_model_sentiment is for the sentiment task). Check train.py to see the options.
* utilities: includes lasagne_average_layer.py, params.py, and tree.py. These provides utility functions/classes for the above two parts. 

## References
For technical details and full experimental results, see [the paper](https://openreview.net/forum?id=SyK00v5xx).
```
@article{arora2017asimple, 
	author = {Sanjeev Arora and Yingyu Liang and Tengyu Ma}, 
	title = {A Simple but Tough-to-Beat Baseline for Sentence Embeddings}, 
	booktitle = {International Conference on Learning Representations},
	year = {2017}
}
```
