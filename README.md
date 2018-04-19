# Comic Book Artist Identifier

This project focuses on distinguishing an artist’s work when presented with an unknown art sample. 

There are a number of challenges in definitively identifying an artist.

The difficulty with comic book artists is that the artist pencils the art which is likely inked over by another artist and colored by yet another artist. In addition, word balloons and narrative may further obscure the art. 

The artist’s style will also change over time or with the subject matter. To further complicate the process, newer artists can be influenced by another artist’s style.


## Data
The project uses Jack Kirby, co-creator of “The Black Panther,” “The Avengers” and many other popular series as the target artist. The initial comparison artists are intended to be stylistically different from Kirby. In this case, Jim Lee, the Co-Publisher of DC Comics, and Randall Munroe, a cartoonist known for his web comic XKCD. In the interest in giving the nueral network a break, XKCD is primarily stick figures.

| Artist  | Example  |
|---|---|
|Jack Kirby| ![kirby](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/jack_kirby.jpg) |
|Jim Lee  | ![lee](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/jim_lee.jpg)|
| Randall Munroe  | ![munroe](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/cat_proximity.png)  |



## Exploratory Data Analysis
Images files (jpg and png) were extracted from Google Images, Pinterest and Tumblr. The images were black and white and usually inked. Lighter pencils were thrown out. The initial pool consists of 1025 jpg and png images proportionally resized and cropped to 200x200 pixels.


## Preprocessing
To prepare the dataset, photos and “homages” were manually removed. File names with spaces and illegal characters were modified to allow the files to be input into the system. The training data was set with labels as the directory name to make adding additional artists easier.

## Initial Neural Network Architecture

The model was generated by Keras using a TensorFlow backend. The architecture is a LeNet Convolutional Neural Network. This returned a poor accuracy of ~25%. With the model overfitting, what are the impacts of each of the layers and their settings?

| Layers  |  Kernel |  Activation |  Pool | Layer  | Kernel  |  Activation | Pool  | Image  |
|---|---|---|---|---|---|---|---|---|
| Original  |   |   |   |   |   |   |   | ![1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/1-original.png)  |
|  3 | 10x10  |   |   |   |   |   |   |  ![2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/2-10x10_convcat.png)  |
|  1 | 3x3  |   |   |   |   |   |   |  ![3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/3-conv2d_3x3_.png)  |
|  1 | 15x15  |   |   |   |   |   |   |  ![4](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/4-conv_15x15.png)  |
|  1 | 3x3  | relu  |   |   |   |   |   |  ![5](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/5-conv3x3_relu.png)   |
|  3 | 3x3  | relu  |   |   |   |   |   |   ![6](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/6-conv_3x3_relu_3filter.png)  |
| 1  | 3x3  |   | 5,5  |   |   |   |   |   ![7](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/7-add_maxpooling.png)  |
|  3 | 3x3  |   | 5,5  |   |   |   |   |   ![8](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/8-3layer_maxpooling.png)  |
|  1 | 3x3  | relu  | 5,5  |   |   |   |   |   ![9](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/9-relu+pool.png)  |
| 3  | 3x3  | relu  | 5,5  |   |   |   |   |   ![10](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/10-relu+pool.png)  |
|  1 | 3x3  | relu  |  3,3 |  1 | 3x3  | relu  |  3,3 |  ![11](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/11-conv+pool_lenet.png)  |
|  3 | 3x3  | relu  |  3,3 |  1 | 3x3  | relu  |  2,2 |   ![12](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/12-lenet2.png)|
|  3 | 3x3  | relu  |  3,3 |  3 | 3x3  | relu  |  2,2 |   ![13](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/13-lenet3.png)  |


Input

CONV => RELU => POOL

CONV => RELU => POOL

FC => RELU

Softmax Classifier

![tensorboard graph](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/tensor_graph.png "Tensorboard Graph")


## Second Model
The next model included 
## Results

(Plot + ROC)
(Example Image Identification)

## Next Steps

## References

## Tech Stack
