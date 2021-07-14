This repo provides the code with paper ["Hierarchical Text Classification with Reinforced Label Assignment"](https://arxiv.org/abs/1908.10419) EMNLP 2019.

<img src="fig/prediction_animation.gif" alt="prediction_animation" style="zoom: 33%;" />

<img src="fig/HiLAP_architecture.jpg" alt="HiLAP_architecture" style="zoom:50%;" />

## Abstract

While existing hierarchical text classification (HTC) methods attempt to capture label hierarchies for model training, they either make local decisions regarding each label or completely ignore the hierarchy information during inference. To solve the mismatch between training and inference as well as modeling label dependencies in a more principled way, we formulate HTC as a Markov decision process and propose to learn a **L**abel **A**ssignment **P**olicy via deep reinforcement learning to determine *where to place* an object and *when to stop* the assignment process. The proposed method, **HiLAP**, explores the hierarchy during both training and inference time in a *consistent* manner and makes *inter-dependent* decisions. As a general framework, HiLAP can incorporate different neural encoders as *base models* for end-to-end training. Experiments on five public datasets and four base models show that HiLAP yields an average improvement of 33.4% in Macro-F1 over flat classifiers and outperforms state-of-the-art HTC methods by a large margin.

## Model

`model.py`: The main model of HiLAP.

`TextCNN.py`: Our implementation of "Convolutional Neural Networks for Sentence Classification" EMNLP 2014.

`OHCNN(_fast).py`: Our implementation of "Effective Use of Word Order for Text Categorization with Convolutional Neural Networks" NAACL 2015.

`HAN.py`: Our implementation of "Hierarchical Attention Networks for Document Classification" NAACL 2016.

`HMCN.py`: Our implementation of "Hierarchical Multi-Label Classification Networks" ICML 2018.

## Requirements

Python **3**

PyTorch **0.3**

## Data

Due to copyright issues, we can't directly release the datasets used in our experiments.
Instead, we provide the links to the five data sources (the first two may require license):

- RCV1 [original release](http://www.ai.mit.edu/projects/jmlr/papers/volume5/lewis04a/lyrl2004_rcv1v2_README.htm), [text data](https://trec.nist.gov/data/reuters/reuters.html) (**update:** download the text data and convert to docs.txt with format "docid content")
- [NYT](https://catalog.ldc.upenn.edu/LDC2008T19)
- [Yelp](https://www.yelp.com/dataset/challenge) (**update:** the latest release is different from what we used, pls send an email if you need the version we used)
- [FunGO](https://dtai.cs.kuleuven.be/clus/hmcdatasets/)

Please check `readData_*.py` to see how to use our scripts to process and generate the datasets from the original data.

## Run
All the parameters in `conf.py` have default values. Change parameters `mode`, `base_model`, and `dataset` and then run `main.py` to train or test on different settings. To test a model, set `load_model=model_file` & `is_Train=False` in `conf.py` and run `main.py`.

## Cite

```
@inproceedings{mao-etal-2019-hierarchical,
    title = "Hierarchical Text Classification with Reinforced Label Assignment",
    author = "Mao, Yuning  and
      Tian, Jingjing  and
      Han, Jiawei  and
      Ren, Xiang",
    booktitle = "Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing (EMNLP-IJCNLP)",
    month = nov,
    year = "2019",
    address = "Hong Kong, China",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/D19-1042",
    doi = "10.18653/v1/D19-1042",
    pages = "445--455",
}
```

