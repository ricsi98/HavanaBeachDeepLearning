# HavanaBeachDeepLearning

For our homework assignment we chose to make a Generative Adversarial Network. Our main goal is to generate pokemons, based on the following dataset: https://www.kaggle.com/kvpratama/pokemon-images-dataset/data. As a possible improvement we would try to make a network that is able to generate pokemons based on drawings, by users.

Preprocessing:

As we are making a GAN we don't need to separate the images to training and validation set, because all the images will be training images.
Also we don't need preprocessing (normalizing), because only the discriminator will use the images to detect whether its input image is a generated "false" image, or an original one. So if we want to generate images like to the original images, we must not change them.
The only preprocessing we made, is that we resized the images (from 256x256 to 64x64), hence the network will train on smaller data, and can converge faster.

To run the .ipynb file it should be in the same folder as the "pokemon" folder, which contains the images.
