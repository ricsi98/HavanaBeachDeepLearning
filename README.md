# HavanaBeachDeepLearning

## First Assignment
For our homework assignment we chose to make a Generative Adversarial Network. Our main goal is to generate pokemons, based on the following dataset: https://www.kaggle.com/kvpratama/pokemon-images-dataset/data. As a possible improvement we would try to make a network that is able to generate pokemons based on drawings, by users.

Preprocessing:

As we are making a GAN we don't need to separate the images to training and validation set, because all the images will be training images.
Also we don't need preprocessing (normalizing), because only the discriminator will use the images to detect whether its input image is a generated "false" image, or an original one. So if we want to generate images like to the original images, we must not change them.
The only preprocessing we made, is that we resized the images (from 256x256 to 64x64), hence the network will train on smaller data, and can converge faster.

To run the .ipynb file it should be in the same folder as the "pokemon" folder, which contains the images.


## Second Assignment
### Model architecture
We built our model based on the [DCGAN](https://arxiv.org/pdf/1511.06434.pdf) architecture. The model has a generator and a discriminator network. We feed a noise (gaussian) vector into the generator network as its input and the output is a 64x64 RGB image. The discriminators input is a 64x64 RGB image and the output is the probability that the input is real.
### Training
The discriminators loss function is the binary-crossentropy of the output probability and the real values (1 or 0). To train the generator we feed the generators output to the discriminator (we call the combined model adverarial) and based on the previous loss we propagate back the error to the generator. 
It is an option to fix the discriminators weights in the adversarial model, so we only update the generators weights. We tried training the model with fixed and not fixed weights as well. 
We tried two training strategies:
1. In each epoch we train the discriminator and the adversarial both.
2. In each epoch we choose which model to train based on their accuracies. (We train only the "weaker" model) - in this case each model is trained until it is as "good" as the other.
### Testing Hyperparameters
We tried mutliple optimizers: adam and rmsprop. Our results can be found in the train1 results folder.
Naming conventions:
* no train - the discriminators weigths are fixed in the adversarial model.
* train - the discriminators weigths are NOT fixed in the adversarial model.
* separately - we used the 1. strategy during training.
* GXM and DXM - D stands for the discriminator, G is the generator. XM means the model has X Million weights.
* the name of the image files specifies the training epoch count.
