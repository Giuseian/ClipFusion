# ClipFusions: Cross-Modal Transformers for Video Question Answering

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/Python-3.9+-yellow.svg)

**ClipFusions** is a cross-modal transformer architecture for tackling Video Question Answering (VideoQA). This project uses pre-trained BERT models for textual understanding and CLIP-based encoders for extracting visual features. It supports multiple-choice question answering across datasets like **TGIF-Action** and **MSRVTT-MC**.

Developed as part of the MSc in Artificial Intelligence and Robotics at Sapienza University of Rome.

## Overview

VideoQA demands multimodal and temporal reasoning across both video and natural language. Unlike static image-based tasks, it requires understanding sequences of visual events, identifying entities and actions over time, and aligning them with complex language queries.

In **ClipFusions**, we address this challenge by developing a cross-modal transformer architecture capable of reasoning jointly over visual and textual modalities. Our approach leverages:

- **Pre-trained BERT-based text encoders** to capture contextual and semantic nuances in language,
- **CLIP-based visual encoders** to extract high-level features from sampled video frames,
- A **two-stage transformer decoder** that integrates question–video and answer–question–video representations to model fine-grained interactions.

We adopt and extend techniques from **ClipBERT** and **VIOLET**, incorporating innovations such as **masked multi-head self-attention**, **positional encodings**, and **late fusion mechanisms** to align multimodal representations effectively.


## Datasets
Our models are evaluated on two standard benchmarks focusing on **multiple-choice question answering (MCQA)**: 

### [MSRVTT-MC](https://github.com/Yale-LILY/MSRVTT-QA)
- Contains ~2,000 short video clips from the MSR-VTT dataset.
- Each video is paired with a question and four answer choices.
- Designed for multi-modal reasoning and multiple-choice evaluation.
- We sample frames uniformly and extract visual features using CLIP.

### [TGIF-Action](https://github.com/YunseokJANG/tgif-qa)
- Contains animated GIFs with corresponding questions and multiple answer choices.
- Designed to test **temporal reasoning** and **spatio-temporal understanding**.
- Questions include actions like “What does the man do after X?”
- Short video lengths simplify temporal alignment and embedding.

Both datasets were preprocessed using custom scripts that (1) extract visual features using CLIP, (2) tokenize and embed textual inputs with BERT, and (3) format question–answer pairs for input into transformer-based multiple-choice QA models.

## Final Observations

Despite dataset limitations, our architecture demonstrates strong performance on training sets and provides insights into the challenges of generalization in multimodal learning.

While models like ClipFusions can effectively align and reason across visual and textual modalities, their performance on unseen test samples highlights the critical importance of dataset diversity, volume, and quality. In particular, the limited size of the TGIF and MSRVTT datasets constrained the model’s ability to generalize to more complex or varied scenarios.

Moreover, experiments revealed that architectural choices—such as the use of lightweight encoders (e.g., DistilBERT) and multi-stage decoding—can significantly influence both performance and computational efficiency. Interestingly, deeper transformer stacks or hybrid encoders did not consistently improve results, suggesting that optimal model depth must be carefully balanced with the complexity of the task and the volume of training data.

Overall, this project reinforces the potential of cross-modal transformers in VideoQA and sets the stage for more robust, scalable, and generalizable multimodal systems.


## References

```bib
@misc{lei2021clipbert,
  title     = {Less is More: ClipBERT for Video-and-Language Learning via Sparse Sampling},
  author    = {Jie Lei and Linjie Li and Luowei Zhou and Zhe Gan and Tamara L. Berg and Mohit Bansal and Jingjing Liu},
  year      = {2021},
  eprint    = {2102.06183},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CV},
  url       = {https://arxiv.org/abs/2102.06183}
}

@article{zellers2021merlot,
  title     = {MERLOT: Multimodal Neural Script Knowledge Models},
  author    = {Zellers, Rowan and Lu, Ximing and Hessel, Jack and Yu, Youngjae and Park, Jae Sung and Cao, Jize and Farhadi, Ali and Choi, Yejin},
  journal   = {Advances in Neural Information Processing Systems},
  volume    = {34},
  pages     = {23634--23651},
  year      = {2021}
}

@inproceedings{jang2017tgifqa,
  title     = {TGIF-QA: Toward Spatio-Temporal Reasoning in Visual Question Answering},
  author    = {Jang, Yunseok and Song, Yale and Yu, Youngjae and Kim, Youngjin and Kim, Gunhee},
  booktitle = {Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages     = {2758--2766},
  year      = {2017}
}

@misc{fu2022violet,
  title     = {VIOLET: End-to-End Video-Language Transformers with Masked Visual-token Modeling},
  author    = {Tsu-Jui Fu and Linjie Li and Zhe Gan and Kevin Lin and William Yang Wang and Lijuan Wang and Zicheng Liu},
  year      = {2022},
  eprint    = {2111.12681},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CV},
  url       = {https://arxiv.org/abs/2111.12681}
}
```

## Authors
- **Giuseppina Iannotti** – `iannotti.1938436@studenti.uniroma1.it`  
- **Maria Emilia Russo** – `russo.1966203@studenti.uniroma1.it`