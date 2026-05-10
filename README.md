# Sentiment-Classification
Developed a deep learning–based Natural Language Processing sentiment classification system to predict whether Internet Movie Database IMDb movie reviews are positive or negative.
Used the IMDb dataset containing 50,000 labeled movie reviews, evenly distributed across:
25,000 positive reviews
25,000 negative reviews
Performed comprehensive text preprocessing, including:
Converting all text to lowercase
Removing HTML tags
Removing special characters and punctuation
Preserving sentiment-critical negation words such as not, never, and no
Normalizing extra whitespace
Encoded sentiment labels into binary format:
Positive → 1
Negative → 0

Split the dataset into:

Training set
Validation set
Test set

using stratified sampling to maintain balanced class distributions.

Tokenized cleaned reviews using Keras Tokenizer and constructed a vocabulary of the 10,000 most frequent words.
Converted reviews into integer sequences and analyzed sequence-length distribution to determine an optimal input size.
Applied sequence padding to a fixed length of 200 tokens so all reviews could be processed uniformly by recurrent neural networks.
Used an Embedding layer to transform each token into a 128-dimensional dense vector representation, enabling the models to learn semantic relationships between words.
Implemented and compared four recurrent neural network architectures:
Simple RNN – baseline model to observe vanishing gradient limitations
Long Short-Term Memory LSTM – designed to capture long-term dependencies
Bidirectional Long Short-Term Memory Bidirectional LSTM – processes sequences in both forward and backward directions
Gated Recurrent Unit GRU – a lightweight and computationally efficient alternative to LSTM
Applied Dropout regularization (0.5) to reduce overfitting and improve generalization.
Conducted hyperparameter experiments by varying:
Number of recurrent layers (1, 2, and 3)
Hidden units (64, 128, and 256)
Dropout rates (0.3, 0.5, and 0.7)
Trained all models using:
Adam Optimization Algorithm Adam optimizer
Binary Cross-Entropy Loss
Batch size of 64
Up to 10 epochs
Used EarlyStopping to monitor validation loss and automatically restore the best-performing model weights.
Evaluated each architecture using:
Test accuracy
Test loss
Training time
Parameter count
Training and validation learning curves
Model Performance Comparison
Simple RNN
Accuracy: 51.47%
Training Time: 11.05 minutes
Parameters: 1,292,417
LSTM
Accuracy: 87.63%
Training Time: 66.03 minutes
Parameters: 1,461,057
Bidirectional LSTM
Accuracy: 84.17%
Training Time: 22.03 minutes
Parameters: 1,420,097
GRU
Accuracy: 88.54% (Best Performing Model)
Training Time: 47.41 minutes
Parameters: 1,416,385
Observed that:
Simple RNN suffered from vanishing gradient issues and failed to capture long-range dependencies.
LSTM significantly improved sentiment understanding by retaining contextual information.
Bidirectional LSTM leveraged both past and future context but required higher computational cost.
GRU achieved the highest test accuracy while maintaining fewer parameters and faster convergence than LSTM.
Validated the final models on custom reviews, confirming robust predictions with confidence scores for both positive and negative sentiments.

Selected the GRU model as the final classifier based on its superior performance and computational efficiency.
