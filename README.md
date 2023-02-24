# KG-VIS

## Introduction 
This repository contains a dataset, *VisBank*, and a named entity recognition (NER) model related to our paper: 
*VIS-KG: Break the Boundaries of Knowledge of Information Retrieval in VIS Literature*

## Data 
The dataset, **VISBank** we constructed in this paper was sourced from https://github.com/allenai/s2orc and comprises 125,745 papers from the visualization literature. It follows the same schema as the S2ORC dataset.


## Named Entity Recognition 
### Training data
We have manually labeled 5076 samples to train the NER model, which can be accessed via https://huggingface.co/datasets/Yamei/NER_VIS_5076. It is straightforward to load the data using the Hugging Face library, as shown below:

```
from datasets import load_dataset
dataset = load_dataset("Yamei/NER_VIS_5076")
```
### NER Model 
The model aims to extract specific named entities from scientific papers in the visualization literature. We have defined five types of entities for visualization literature, namely data, application, visualization, method, and evaluation. We have fine-tuned five models on our training data, and they are publicly available at https://huggingface.co/Yamei. Below is an example of how to use our model:
```
from transformers import pipeline
hub_model = "Yamei/scibert_scivocab_uncased-v10-ES-ner"
classifier = pipeline("ner", model=hub_model)
text = f"""
However, in situ visualization approaches limit the flexibility of post-hoc exploration because the raw simulation data are no longer available.
"""
result = classifier(text)
```

Alternatively, you can also try the model directly from the Hugging Face website.
![image](https://user-images.githubusercontent.com/18289816/221269081-cde3429f-ba21-4807-a733-6a5ed64ab076.png)

## Knowledge Graph 
The constructed 
