# Colorization
###### Image and Video Processing Course Project

This project aims to accomplish and explore the problem of designing an automatic system to colorize given grayscale images with plausible colors. This project focus on deep learning techniques based on Convolve Neural Network and the basic idea of this project is from [Richard Zhang's project](http://richzhang.github.io/colorization/). The images in this project are treated in LAB mode. We treat the problem as a regression task and classification task respectively. The result shows that colorization could be accomplished better as a classification problem. On top of that, we try different methods to improve the system. For example, rebalancing the weight of loss function, filtering the output, adding batch normalization and dropout layers to the model. To make the result more intuitive, several models were trained and compared. Details of each model and the applied method are listed in the following table.

|Model|Method|
|--|--|
|1|Regression|
|2|Classification|
|3|Classification, class weight|
|4|Classification, class weight, Conv2DTranspose|
|5|Classification, class weight, Batch Normalization and Drop Out|
|6|Classification, class weight, Conv2DTranspose, Batch Normalization and Drop Out|

## Results
The training images are from [ImageNet](http://image-net.org/) and the [Oxford Buildings Dataset](http://www.robots.ox.ac.uk/~vgg/data/oxbuildings/). We reshaped them into 64 by 64 pixels. For each category of images, we use a training size of 400 and a testing size of 200 for validation. To compare the result of each model, we train them using the same bath size of 32 and runing 100 epochs.The most typical results shown below are from the image category [Pasqueflower](https://github.com/tqiongxuan/Colorization/tree/master/pasqueflower). 

![Pasqueflower Result](https://github.com/tqiongxuan/Colorization/blob/master/Pasqueflower.png)


To see how robust the models are, we train them on different image categories. In some case (i.e., [Alp](https://github.com/tqiongxuan/Colorization/tree/master/alp) and [Oxford Building](https://github.com/tqiongxuan/Colorization/tree/master/oxford)) they work as expect, but some (i.e., [Flora](https://github.com/tqiongxuan/Colorization/tree/master/flower)) they fail. The models work well when the images have simple similar features. When the features become complicated or without similarity, the resulting color images are unreasonable.

![Different Image Categories](https://github.com/tqiongxuan/Colorization/blob/master/alp_oxfoed_flower.png)

## Conculsion
We concule that the task of coloring black and white images using an encoder-decoder style CNN, can be done if we treat is as a classification problem and use categorical cross-entropy as loss function. It works well when the testing images and training images share some similarity, for example images of the same species or similar scene. Simply use regression approach to predict values of a and b channel gives poor results. The classification model can be improved by rebalancing the class weight and replacing the “UpSampling2D” layers by “Conv2DTranspose”. Applying batch normalization and drop out can reduce overfitting but yields worse colorization quality. To reduce the artifact in a predicted color image, one can apply Gaussian filters to the color channels.

## Authors
Qiongxuan Tan
Xiaotian Pang
