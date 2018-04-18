# Comic Book Artist Identifier

This project focuses on distinguishing an artist’s work when presented with an unknown art sample. 

There are a number of challenges in definitively identifying an artist.

The difficulty with comic book artists is that the artist pencils the art which is likely inked over by another artist and colored by yet another artist. In addition, word balloons and narrative may further obscure the art. 

The artist’s style will also change over time or with the subject matter. To further complicate the process, newer artists can be influenced by another artist’s style.


## Data
The project uses Jack Kirby, co-creator of “The Black Panther,” “The Avengers” and many other popular series as the target artist. The initial comparison artists are intended to be stylistically different from Kirby. In this case, Capullo, the current artist on “Batman” and other high profile series, and Sergio Aragones, a cartoonist known for his work in Mad magazine. 



## Exploratory Data Analysis
Images files (jpg and png) were extracted from Google Images and Tumblr. Images included pencils, inked black and white art and color art. The Kirby sample was made up of XX images, the Capullo sample was made up of  XX images and the Aragones sample was made up of XX images. (The image counts should probably be evened out to prevent class imbalance.)

## Preprocessing
To prepare the dataset, photos and “homages” were manually removed. File names with spaces and illegal characters were modified to allow the files to be input into the system. The training data was set with labels as the directory name to make adding additional artists easier.

Files were broken apart into 50 x 50 images and rotated and flipped to eliminate (bias?).

(TensorBoard Image layer examples)


## Neural Network Architecture

The model was generated by Keras using a TensorFlow backend. The architecture is a LeNet Convolutional Neural Network.

Input

CONV => RELU => POOL

CONV => RELU => POOL

FC => RELU

Softmax Classifier

![tensorboard graph](https://github.com/rhaussmann/ds-capstone-2/img/tensor_graph.png "Tensorboard Graph")


## Results

(Plot + ROC)
(Example Image Identification)

## Next Steps

## References

## Tech Stack
