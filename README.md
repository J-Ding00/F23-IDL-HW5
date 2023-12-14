# F23-IDL-HW5
The git repository to F23 11685 Intro to Deep Learning homework 5

We were able to concatenate all files (excluding data collecting and processing) into this 11685-hw5.ipynb file.
It includes our pre-train and fine-tune dataset, dataloader, model, training hyperparameters, valuation functions, train and validate functions and so on.

Wandb: https://wandb.ai/jding3/hw5-ablations?workspace=user-jding3

Training dataset
We trained our pretrain model with OpenWebTextCorpus obtained from (https://skylion007.github.io/OpenWebTextCorpus/), an open source effort to reproduce OpenAI’s WebText dataset. The dataset was produced beginning by collecting Reddit post URLs, followed by deduplication and filtering to exclude non-HTML content. Web pages were extracted using the newspaper Python package. Non-English pages were filtered out using Facebook FastText. Local-sensitivity hashing (LSH) identified near-duplicate documents based on 5-gram sets. The remaining documents were tokenized, and resulting in a final dataset of 38GB of text from 8,013,769 documents.

Model
We used a transformer based architecture for our pre-train and fine-tuned model. Refering to GPT-2 and Nano-gpt, Our model first performs vocab-token embedding and positional embedding on the given data, followed by 6 Transformer blocks which contains a LayerNorm1d layer, 6-heads multi-head attention block in which it contains a query, key, and value linear layer, softmax layer, and dropout layer each. Following the multi-head attention block, there’s a linear projection for the concatenated outputs from previous heads-module. Other layers in Transformer blocks are dropout and layerNorm layers. The last component of the Transformer block is the feed forward network. It contains 2 fully connected layers with a GELU activition layer in between them. Last but not least, after the Transformer blocks, there’s a LayerNorm layer followed by a final classification layer that projects the embedded symbols back to vocab logits.

Total params 88.051625M
