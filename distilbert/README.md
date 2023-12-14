# sentiment.md

In this notebook, we use language models to predict the sentiment of a given movie review. The dataset is sampled from the [IMDB dataset of 50k movie reviews](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews). The sentences are sampled to a smaller set to help with quicker computation on Colab. The data contains a review and an associated _positive_ or _negative_ sentiment label. The training, validation, and test data is used to fine-tune the models, select the best model while training, and measure performance, respectively. To perform this task, we use a pre-trained DistilBERT model, a BERT-based language model that is 40% smaller, 60% faster, but retains 97% of BERT's performance, from Hugging Face, as follows:

1. Load a pre-trained DistilBERT model and its tokenizer using Hugging Face's `AutoTokenizer` and `AutoModelForSequenceClassification` classes, adapting the model to the task of sentiment analysis.
2. Tokenize the reviews and convert the labels into numerical classes by using the `tokenizer.encode_plus` method, which takes in a review and returns a dictionary that contains the tokenized review as a Tensor; convert labels to a numerical class using the label_dict dictionary.
3. Set the layers of the model to be trained based on the `training_type` by iterating over the named parameters of the model and setting `requires_grad=False` for the layers that are not to be trained. The classifier head on top of the final DistilBERT layer is always trained, so this layer is always set to be trainable.
4. Train the model, updating parameters by backpropagating the loss.
5. Validate and test the model by computing the Precision, Recall, and F1.

The training types are:

- frozen_embeddings: All layers are frozen.
- top_2_training: Only the last two layers are trained.
- top_4_training: Only the last four layers are trained.
- all_training: All layers are trained.
