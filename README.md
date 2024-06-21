# Image-Caption
Image captioning is the task of generating textual descriptions for images. It combines techniques from computer vision and natural language processing. An effective approach to image captioning is using auto-encoders, specifically a combination of convolutional neural networks (CNNs) and recurrent neural networks (RNNs), implemented in PyTorch.

This project is a hands-on exploration of image captioning, where a model generates descriptive sentences for given images.

# Dataset
We use the Flickr30k dataset available on Kaggle.

# Model
The model utilizes a pre-trained ResNet-50 as the image encoder and combines LSTM with stacked GPT-1 blocks as text decoders. The focus is primarily on the text generation part.

Image Encoder: The last layer of ResNet-50 is removed and replaced with a linear layer to match the embedding size of the word embeddings. The output of this encoder initiates the sequence for the text decoder.
Text Decoder: The GPT-1 architecture is simulated using a Transformer Encoder with masks.
All model definitions can be found in model.py.

# Setup
This project is implemented using PyTorch 2.0.1. The experiments are conducted on a Linux machine equipped with an Nvidia Tesla V100-SXM2 GPU with 32 GB memory, using CUDA version 11.7 and Driver version 515.65.01.

# Configurations
The configuration details and hyperparameters are specified in config.py.

# Building Vocabulary
To build the vocabulary, execute:

bash
Copy code
python vocab.py
This process sets up four special tokens: <pad>, <sos>, <eos>, and <unk>, and saves the word2index file.

Training the Model
To train the models, run:

bash
Copy code
python train.py --model [decoder]
You can specify 'lstm' or 'gpt1' as the text decoder. The trained models will be saved in the ./src directory.

Testing an Instance
To test a single instance, run:

bash
Copy code
python show_instance.py --model [decoder] --image_file [file]

# Use Case
* Some detailed usecases would be like an visually impaired person taking a picture from his phone and then the caption generator will turn the caption to speech for him to understand.
*  Advertising industry trying the generate captions automatically without the need to make them seperately during production and sales.
*   Doctors can use this technology to find tumors or some defects in the images or used by people for understanding geospatial images where they can find out more details about the terrain.

Select the model and the image file from your image directory to generate a caption.
