# F23-IDL-HW5
The git repository to F23 11685 Intro to Deep Learning homework 5

We were able to concatenate all files (excluding data collecting and processing) into this 11685-hw5.ipynb file.
It includes our pre-train and fine-tune dataset, dataloader, model, training hyperparameters, valuation functions, train and validate functions and so on.

Wandb: https://wandb.ai/jding3/hw5-ablations?workspace=user-jding3

Training dataset
We trained our pretrain model with OpenWebTextCorpus obtained from (https://skylion007.github.io/OpenWebTextCorpus/), an open source effort to reproduce OpenAI’s WebText dataset. The dataset was produced beginning by collecting Reddit post URLs, followed by deduplication and filtering to exclude non-HTML content. Web pages were extracted using the newspaper Python package. Non-English pages were filtered out using Facebook FastText. Local-sensitivity hashing (LSH) identified near-duplicate documents based on 5-gram sets. The remaining documents were tokenized, and resulting in a final dataset of 38GB of text from 8,013,769 documents.

Model
Layers         Kernel_size
tok_embedding [384, 100264]
pos_embedding [384, 100]
  Transformer_blocks x 6
  LayerNorm [384]
  Heads Self-attention x 6
    Query.Linear [384, 64]
    Key.Linear [384, 64]
    Value.Linear [384, 64]
    Softmax -
    Dropout -
  Multi-Head_Concat.Linear_projection [384, 384]
  Dropout -
  LayerNorm [384]
  Feed_forward.Linear [384, 1536]
  GELU -
  Feed_forward.Linear [1536, 384]
  Dropout -
Final_CLS_LayerNorm [384]
Final_Linear_CLS [384, 100264]

Total params 88.051625M
