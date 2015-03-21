Kmeans Clustering for fruit images
==================================

I use the tiny image data from Data Access Layer(DAL) https://github.com/cioc/DAL, which is a library that makes it easy to use the datasets. 

For this project, I use two evaluation collection. The first one is small, including 200 images, while the other collection is larger, including 10,000 images and only being visible on Amazon Web Service(AWS). 

The following bit of simple code to show how to extract and display them.

```python
from DAL import create
#create a handle to the tinyimages dataset
tinyimages = create('tinyimages')
idS = tinyimages.labelled(’small’)
idL = tinyimages.labelled(’large’)

#load in tinyimages for locally small collection
Simages = tinyimages.byid(idS)

#display small images collection
tinyimages.display(Simages)
```

Procedures
==========

Initially, I need to transform the 32*32 pixels images dataset to 960 gist-component like dataset, which could be expressed as numpy nested arrays. Then we normalize each gists across whole data set in order to make the Kmeans clustering easier.  

In next step, I use the k-means algorithm on the local small collection with several sets of random starting points, pick the set with the least distortion and visualize my resulting clusters. 

Finally, I have implement paralized version k-means to large imgaes collection on AWS and plot the distortion with the number of clusters.