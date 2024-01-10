# Image Caption Generator

This project implements an Image Caption Generator using a pre-trained model. The generator takes an image as input and produces a descriptive caption for the image.

Model Architecture:

1. Encoder (VGG16 for feature extraction):
   - Input: Image with shape (None, 224, 224, 3)
   - Output: Image features with shape (None, 4096)

2. Decoder:
   - Image Feature Input: Features from the encoder with shape (None, 4096)
   - Text Input: Padded sequences of word indices with shape (None, max_length)
   - Embedding Layer: Converts word indices to dense vectors with shape (None, max_length, 512)
   - Bidirectional LSTM Layer: Processes embedded sequences bidirectionally with shape (None, 512)
   - Concatenation: Combines image features and sequence features with shape (None, 1024)
   - Dense Layer: Applies a dense transformation with shape (None, 512)
   - Output Layer: Produces word probabilities with shape (None, vocab_size) using softmax activation

3. Model Inputs and Outputs:
   - Inputs: [Image Feature Input, Text Input]
   - Outputs: Word probabilities for the next word in the sequence

4. Training Details:
   - VGG16 layers are frozen during training to use pre-trained image features.
   - Adam optimizer is used with a learning rate of 0.0001.

Note: Adjustments may be needed based on specific dataset characteristics, vocab_size, and other project requirements.
