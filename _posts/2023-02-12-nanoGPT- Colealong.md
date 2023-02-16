---
layout: post
title:  "nanoGPT"
date:   2023-02-13 
categories: notes
learning_platform: 
specialization: 
course: 
tags: 
---

# Notes from Andrej Karpathy's NanoGPT codealong

* ChatGPT
  * generates text - left to right
  * is a probabilistic system
  * stands for Chat "Generatively Pre-trained transformer"
  * is a language model - it models the sequence of characters or words or token. It predicts how charactes/words/tokens follow each other in a language
  * given a question/prompt, ChatGPT is completing the sequence.
  * is based on the transformer architecture (see the 2017 landmark paper,  attention is all you need)

* NanoGPT
  * trained on [OpenWebtext]
  * reproduces GPT2 124 Million parameter model

Codealong: ~NanoGPT
  * is a character level language model
  * trained on Tiny Shakespeare
  * generates infinite Shakespeare

## Tokenization
* character level
  * used in the codealong
* word level
* sub-word level
  * Google Sentence piece
  * OpenAI tiktoken (used in GPT)

tradeoff codebook size and sequence lengths: with word level or sub word level tokenization, there are a larger number of tokens, but this results in much more compact encoding.

## Training
* Training happens on: 
  * on chunks of data of given blocksize (or context length)
    * In each block, there are 'blocksize' number of individual "contexts"
    * the blocksize gives us the 'time' component (?)
  * on chucks of given batchsize. 
    * Chunks are trained independently

## Bigram Language Model
 * See makemore series


## Jupyter Notebooks

## Links
* [Andrej Karpathy's site](https://karpathy.ai)
* [Karpathy - Makemore Tutorial Playlist](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)

## Links (specific to codealong)

* [ChatGPT Prompt/Response Library](https://www.emergentmind.com)
* [Attention is all you need](https://arxiv.org/abs/1706.03762)
* [Tiny Shakespeare](https://github.com/karpathy/char-rnn/blob/master/data/tinyshakespeare/input.txt)
* [nanoGPT](https://github.com/karpathy/nanoGPT)
* [OpenWebText](https://skylion007.github.io/OpenWebTextCorpus/)
* [GPT 2 weights released by OpenAI](https://openai.com/blog/gpt-2-1-5b-release/)
* [Sentence piece](https://github.com/google/sentencepiece)
* [Tiktoken](https://github.com/openai/tiktoken)
* 


## To Do

* walkthrough the makemore playlist
* revist this lecture from timestamp 25
