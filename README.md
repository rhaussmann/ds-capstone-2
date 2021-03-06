# Comic Book Artist Identifier

This project focuses on distinguishing a comic book artist’s work when presented with an unknown art sample. 

Comic book art presents a number of unique difficulties in identification. 

Typically, the artist pencils art which is inked over by another artist and colored by yet another artist. In addition, word balloons and narrative may further obscure the art or falsly register as part of the art. 

The artist’s style will also change over time or with the subject matter. To further complicate the process, newer artists can be influenced by another artist’s style.


## Data
The project uses Jack Kirby, co-creator of “The Black Panther,” “The Avengers” and many other popular series as the target artist. For demonstration purposes, the other cartoonist that the work is being compared to is Randall Munroe, known for his web comic XKCD. In the interest in giving the nueral network a chance of success, XKCD is primarily composed of stick figures.


## Exploratory Data Analysis
Images files (jpg and png) were extracted from Google Images, Pinterest and Tumblr. The images were black and white and usually inked. Lighter pencils were thrown out. The initial pool consists of 1025 jpg and png images proportionally resized and cropped to 200x200 pixels.

To prepare the dataset, photos and “homages” were manually removed. File names with spaces and illegal characters were modified to allow the files to be input into the system. The training data was set with labels as the directory name to make adding additional artists easier.


| Artist  | 1  |2 |3|4 |
|---|---|---|---|---|
|Jack Kirby| ![kirby1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kirby989.jpg) |![kirby2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kirby1001.jpg) |![kirby3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kirby1004.jpg) |![kirby1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kirby1008.jpg) |
| Randall Munroe  | ![munroe1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xkcd101.jpg)  |![munroe2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xkcd102.jpg)  |![munroe3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xkcd1012.jpg)  |![munroe4](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xkcd1016.jpg)  |

## Process
Initially, the project tried to identify between three artists but it proved too difficult with a mixture not only of artists but with the addition of color as well. Sample images were increased to their current size from 50x50 (grouped by original image and returning votes for the class). Larger, complete images were expected to show patterns better than smaller pieces. Various models were tested to try to eliminate overfitting but for this analysis, the simpler LeNet Convolutional network (developed for handwriting) was used.


## Tracking Filters Through the Architecture

The model was generated by Keras using a TensorFlow backend. The architecture is a LeNet Convolutional Neural Network. This returned a poor accuracy of ~50%. With the model overfitting, what are the impacts of each of the layers and their settings?
Here are the layers and their cumulative effects on the image.

| Layers  |  Image| 
|---|---|
| Original  |![0](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kirby989.jpg)  |
|Convolution: Conv2D : filter:20 kernel: 5x5 |![1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f1.png)|
|Activation: ReLU |![2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f2.png)|
|Pooling: MaxPooling2D: Pool:2x2 Strides: 2x2 |![3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f3.png)|
|Convolution: Conv2D : filter:50 kernel: 5x5  |![4](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f4.png)|
|Activation: ReLU |![5](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f5.png)|
|Pooling: MaxPooling2D: Pool:2x2 Strides: 2x2 |![6](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/f6.png)|
|Flatten + Dense(500) + Activation:ReLU||
|Dense(2)+Activation: Softmax||




![tensorboard graph](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/tensorboard.png "Tensorboard Graph")


## Second Model
The next model uses .L2 regularization, ensembles and batch normalization. 
The results: 0.9744 - acc: 0.8072.

## Results

| Accuracy| Loss |
|---|---|
|![acc](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/acc.png)|![loss](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/loss.png)|

## Predictions

| Artist  | 1  |2 |3|4 |
|---|---|---|---|---|
|Jack Kirby| ![kirby1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kr1.png) |![kirby2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kr2.png) |![kirby3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kr3.png) |![kirby1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/kr4.png) |
| Randall Munroe  | ![munroe1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xr1.png)  |![munroe2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xr2.png)  |![munroe3](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xr3.png)  |![munroe4](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/xr4.png)  |
|Jim Lee|![lee1](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/lr1.png)|![lee2](https://github.com/rhaussmann/ds-capstone-2/blob/master/img/lr2.png)|||

## Next Steps

Additional fine tuning techniques: Batch Normalization, L2 Regularization, Ensembles, Early Stopping
Additional CV2 Filters: Canny Edge Detection

## References

[AI Machine Attempts to Understand Comic Books ... and Fails](https://www.technologyreview.com/s/602973/ai-machine-attempts-to-understand-comic-books-and-fails/)

[Detecting comic strip dialogue bubble regions in images](https://stackoverflow.com/questions/34356635/detecting-comic-strip-dialogue-bubble-regions-in-images)

Rosebrock, Adrian. [Image classification with Keras and deep learning](https://www.pyimagesearch.com/2017/12/11/image-classification-with-keras-and-deep-learning/)

Wilkins, Benjamin. [Sketching Interfaces: Generating code from low fidelity wireframes](https://airbnb.design/sketching-interfaces/)

Ueno, Miki. [Comic Book Interpretation based on Deep Neural Networks] (http://www.ttic.edu/SNL2017/papers/SNL-2017_paper_19.pdf)

Uenoa, Miki, et al. [Classification of Two Comic Books based on Convolutional Neural Networks](https://gredos.usal.es/jspui/bitstream/10366/133632/1/Classification_of_Two_Comic_Books_based_.pdf)


