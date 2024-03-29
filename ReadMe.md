## Kaggle Challenge 

## Ultrasound Nerve segmentation 

### Aim 

The nerve area called the brachial plexus needs to be segmented from the given images. This was a challenging problem since there were an uneven distribution of images with masks. Some of the kernels had pointed out data with contradictory masks.Therefore a simple thresholding could eliminate these images. 

### Image Preprocessing 

The image format was .tif and 580x420 in size.Therefore it is too big to be trained on my GPU. I have decided to rescale my images size 128x128 since it is faster to predict and train. I tried with all the training images initially for seeing what performance the data set without any augmentation provides. It gave a private score .53. The improvements occurs  with augmentation and checking for those contradictory masks for the similar images. 
![j](https://user-images.githubusercontent.com/25079132/61428893-1cc90980-a8f2-11e9-8308-548a0b3d4a2d.JPG)

![m](https://user-images.githubusercontent.com/25079132/61429093-ed66cc80-a8f2-11e9-8bad-89632e6818b6.JPG)


## Image Similarity 

This training set had many contradictory images . Histogram intensity can be found using 

```
###spatial distance using cosine similarity
    import scipy.spatial.distance as spdist
    D = spdist.squareform(spdist.pdist(x, metric='cosine'))

```
![similairty](https://user-images.githubusercontent.com/25079132/64492231-f06da180-d23f-11e9-9b5e-b31b692e1598.JPG)

### Model Selection 

A unet is always best for segmentation especially for a biomedical image analysis. I decided to use a Unet without pretrained weightsand used Dropouts in between to increase acuracy.The loss function used is a dice score which can be used for checking for overlap beween ground truth makss and predicted masks.

![unetmodel](https://user-images.githubusercontent.com/25079132/64492339-f912a780-d240-11e9-9328-98f9317d6cb1.JPG)

#### To do 

Currently trying to implemnt a FCNN model , will update soon 
