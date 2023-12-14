# sentiment.ipynb

A few-shot learning approach with a GPT model, such as the one used in this task, text-davinci-003, aims to leverage the model's pre-existing knowledge and adapt it to perform a specific task with just a few examples, as opposed to traditional machine learning methods that require large amounts of labeled data to train. This saves time and resources as it does not require extensive fine-tuning. We used text-davinci-003 because it is the most powerful GPT model available at the time of writing.

In this task, the objective is to classify the sentiment of a text towards a specific main subject. The few-shot learning approach involves providing the GPT model with a few labeled examples from the training dataset, followed by the target text and main entity. The examples are formatted as a prompt, which is then fed to the model. The model then (essentially) learns from the examples and applies it to the target text.
