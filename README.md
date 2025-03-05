# English-to-Traditional-Chinese-using-sequence-to-sequence-Machine-Translation
This repository contains the code for a sequence-to-sequence machine translation project that translates English sentences into Traditional Chinese. The project is based on a simple RNN seq2seq architecture with key enhancements including sub-word tokenization, label smoothing regularization, and a learning rate scheduler.

Overview
The goal of this project is to translate English sentences into Traditional Chinese using a sequence-to-sequence model. The model is composed of an encoder and a decoder:

Encoder: Encodes the input English sentence into a vector (or sequence of vectors).
Decoder: Decodes one token at a time, conditioned on the encoder output and the previously generated tokens.
![image](https://github.com/user-attachments/assets/e7e5b40f-5959-46f1-994d-59bd2205b085)


Dataset : (https://drive.google.com/file/d/1Sys5keuiw4C27_cG3LMyYi6v5eHJvu1L/view)
Training Data:
train_dev.raw.en: 390,112 English sentences
train_dev.raw.zh: 390,112 corresponding Traditional Chinese sentences
Test Data:
test.raw.en: 3,940 English sentences
The Chinese test translations are undisclosed (the provided .zh file is pseudo translation).
Key Components
1. Sub-word Tokenization
Purpose:
Reduce vocabulary size and address out-of-vocabulary (OOV) issues.
Method:
Words are split into common prefixes and suffixes.
This helps in handling rare words and morphological variations (e.g., "new", "_new", "_ways", etc.).
2. Label Smoothing Regularization
Purpose:
Reserve some probability mass for incorrect labels during loss calculation.
Benefit:
Reduces overfitting and improves generalization during training.
![image](https://github.com/user-attachments/assets/b4f28bdf-9747-457b-9489-2a53e329014e)


3. Learning Rate Scheduling
Implementation:

The learning rate increases linearly for the first warmup_steps and then decreases proportionally to the inverse square root of the step number.
Benefit:

Stabilizes training, especially in the early stages of training with transformer-based architectures.
![image](https://github.com/user-attachments/assets/140dccd9-8540-46dd-a6c2-f1cf3a414532)


Training and Evaluation
Benchmark Model:

A simple RNN seq2seq model is implemented.
Expected running time is around 0.5 hours for data processing and 0.5 hours for model training.
The benchmark model achieves a BLEU score of approximately 15.
Improvements:

Hyperparameters such as the number of epochs, encoder/decoder layers, and embedding dimensions have been tuned.
A learning rate scheduler is integrated to further stabilize and improve training performance.
Evaluation Metric:

BLEU score is used for evaluating translation quality by measuring the modified n-gram precision (n=1~4) with a penalty for short sentences.
Code Structure
Notebook:

Week6_ap2938DL (1).ipynb – Contains the full implementation including data processing, model definition, training, and prediction for machine translation.
Key Sections in the Notebook:

Data Preprocessing: Loading and tokenizing the English and Chinese datasets using sub-word units.
Model Definition: Implementing the seq2seq model (encoder and decoder) with label smoothing regularization.
Training Loop: Training the model with a learning rate scheduler and tuning hyperparameters.
Evaluation: Generating translations and computing the BLEU score.
Conclusion
This project demonstrates the application of sequence-to-sequence models for machine translation from English to Traditional Chinese. By incorporating sub-word tokenization, label smoothing, and learning rate scheduling, the model achieves improved performance and training stability. All code, experiments, and generated predictions are provided in this repository.
