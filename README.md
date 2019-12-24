# Image Captioning

This notebook uses Flickr8k for training and testing image captioning model.

The files are first extracted, and converted to dictionaries and dataframes for easier operations and for better readability.
The captions are stripped of punctiations, numbers and single letter words for better recognition and predictions of captions by the model and the "clean text" is returned.
The captions are added with "startseq" and "endseq" att he starting and ending of the text respectively, for the model to identify the starting and ending of the captions.
`images` is an ordered dictionary containing the predictions made by the VGG16 model, which are used to test the final model.
The caption texts are converted to an array of integers using Tokenizer, which is similar to the preprocessing of an image into an integer array.
The text-converted-integer arrays are then preprocessed along with the images and are converted into sequences using `pad_sequences` and the output texts are converted to binary matrices using `to_categorical`.
These preprocessed texts and images are split into training, testing and validation sets for the final model to accurately make predictions about the image.


Normally, a CNN will be made of `Convoluted` or `Dense` layers, but for image captioning, a CNN with `Dense` layer (embedding layer) is used as a base for the `LSTM` layer.
The image is embedded as the initial state of the LSTM. Each time, this layer considers the previous state and predicts the output for the next value (next letter/word of the caption in this case).
