Fruit Images
============

I use the tiny image data from Data Access Layer(DAL) https://github.com/cioc/DAL, which is a library that makes it easy to use the datasets. 

For this project, I work with two evaluation collection. The first one includes 200 images, while the other collection contains 10,000 images and only being visible on Amazon Web Service(AWS). 

The following bit of simple code to show how to extract and display them.

```python
from DAL import create

# Create a handle to the tinyimages dataset
tinyimages = create('tinyimages')

# Load in tinyimages for locally small collection
idS = tinyimages.labelled(’small’)
Simages = tinyimages.byid(idS)

# Display small images collection, will show all tiny images in the collection 
tinyimages.display(Simages)
```

Kmeans on local small collection
================================

Initially, I transform the 32*32 pixels images dataset to 960 gist-component like numpy nested array. Then I normalize each gist across whole data set in order to make the k-means clustering easier.  

In next step, I use the k-means algorithm on the local small images collection with random starting points, pick the least distortion result and visualize my resulting clusters. 

From the clustering result, the preformance to classify the banana and tomato is getting better with bigger K, the number of cluster. However, if K goes too large, clustering would be meaningless, for example every image has it's own cluster. When K is 5 or 6, even though there are clusters with half misclassified fruit, the last two clusters have prefect classification result. Hence, in my opinion, the optimal number of K for this dataset is 5 or 6.

Kmeans on AWS large collection
================================

Finally, I implement paralized version k-means to large images collection on AWS. Since there are too many images to visualize, I just plot the distortion of clustering against the value of K.

Due to the premission to data, the plot for large collection on AWS is missing. I will fix it as soon as I get the permission to access the data.

Please check the notebook here for detail:

http://nbviewer.ipython.org/github/eddieyue/Kmeans-clustering-to-classify-fruit-images/blob/master/Kmeans%20Clustering%20to%20classify%20Fruit%20Pictures.ipynb