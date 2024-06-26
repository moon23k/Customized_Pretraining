## Customized Pre-Training

> This repository shares a set of codes for customized pre-trained model tailored to specific tasks. The training objectives for pre-training consist of three components: Masked Language Modeling, Casual Language Modeling, and Masked Casual Language Modeling.
To comprehensively evaluate natural language generation capabilities for each approach, three tasks have been chosen: machine translation, dialogue generation, and document summarization. The goal is to examine how performance fluctuates across diverse tasks when utilizing the pre-trained model.

<br><br>


## Pretraining Objective

### Masked Lanugage Modeling

> Utilizing a logic similar to that employed in BERT, we implement the Masked Language Modeling approach. Masking is applied to only 20% of the entire corpus, excluding Special Tokens. The objective is to enhance bidirectional understanding of the provided corpus. The model structure for Masked Language Modeling includes a Transformer Encoder with an added Pooler.
The pre-trained Encoder will be utilized in the subsequent training process.

<br>

### Casual Lanugage Modeling

> This is a Casual Language Modeling approach that utilizes both an encoder and a decoder. The input values and labels for the model are identical, and the model learns the predicted distribution of the next word given the previous word.
In this pre-training approach, both the encoder and decoder are trained during pre-training, and in the subsequent training process, both the encoder and decoder are used as they are.

<br>

### Masked Casual Lanugage Modeling

> This approach is a combination of the previously discussed Masked Language Modeling and Casual Language Modeling. Essentially, it is Casual Language Modeling, but with some of the input values masked. Both the encoder and decoder are employed in pre-training, and in the subsequent training, both the encoder and decoder are used as they are.

<br><br>



## How to Use
```
├── ckpt                    --this dir saves model checkpoints and training logs
├── pt_ckpt                 --this dir saves pretrained model checkpoints and training logs
├── config.yaml             --this file is for setting up arguments for model, training, and tokenizer 
├── data                    --this dir is for saving Training, Validataion and Test Datasets
├── model                   --this dir contains files for Deep Learning Model
│   ├── __init__.py
│   └── transformer.py
├── module                  --this dir contains a series of modules
│   ├── data.py
│   ├── generate.py
│   ├── __init__.py
│   ├── model.py
│   ├── test.py
│   └── train.py
├── README.md
├── run.py                 --this file includes codes for actual tasks such as training, testing, and inference to carry out the practical aspects of the work
└── setup.py               --this file contains a series of codes for preprocessing data, training a tokenizer, and saving the dataset.
```

<br>

**First clone git repo in your local env**
```
git clone https://github.com/moon23k/CPT_Training
```

<br>

**Download and Process Dataset via setup.py**
```
bash setup.py -task [all, translation, dialogue, summarization]
```

<br>

**Execute the run file on your purpose (search is optional)**
```
python3 run.py -task [translation, dialogue, summarization] \
               -mode [pretrain, train, test, inference] \
               -lm_type [mask, casual, masked_casual] \
               -search [greedy, beam]
```


<br><br>

## Reference
* [**Attention is all you need**](https://arxiv.org/abs/1706.03762)
* [**BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding**](https://arxiv.org/abs/1810.04805)
<br>
