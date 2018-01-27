# Project 2 - SEEDS
## Domain
Measurements of geometrical properties of kernels belonging to three different varieties of wheat. A soft X-ray technique and GRAINS package were used to construct all seven, real-valued attributes.The kernels of three varieties of wheat were examined under soft X- ray technology and a number of geometric properties were recorded. The X- ray technology is non-destructive and substantially cheaper than other imaging technologies and could possibly be used as a means to identify the variety of wheat.

This problem uses measurements of geometrical properties of kernels belonging to three different varieties of wheat. As described in the paper "Comple te Gradient Clustering Algorithm for Features Analysis of X-Ray Images" by Małgorzata Charytanowicz, Jerzy Niewczas, Piotr Kulczycki, Piotr A. Kowalski, Szymon ŁukasikS, Slawomir Żak, published in Advances in Intelligent and Soft Computing [paper](https://link.springer.com/chapter/10.1007/978-3-642-13105-9_2), machine learning is an effective at recognizing different types of wheat grains.

## Problem Statement
Tom Mitchell, a well regarded machine learning researcher, proposed precise definition in 1998:
**Well posed Learning Problem:** A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.

Inputs to our Problem is 3 types of wheat seeds data (as listed in UCI machine learning repository). The machine learning algorith we intend to apply is an Unsupervised Learning. *The algorithm looks for structure in the training data, like finding which examples are similar to each other, and group them in clusters.* such as k-means to cluster the measured samples of wheat grains. 
In our dataset we have 7 attributes of 3 types of wheat samples. 
Objective of the analysis is to find a distinct relation between the physical attributes of wheat seeds and the type of wheat.


## Dataset 

The Dataset provided from UCI machine learning repository http://archive.ics.uci.edu/ml/datasets/seeds
![capture](https://user-images.githubusercontent.com/33742913/35468422-0bf0cade-02d2-11e8-9ac6-7d186753bf7b.PNG)

Data Set Characteristics: Multivariate

- Number of Instances: 210

- Number of Attributes: 7

- Data Type for our dataset is Numeric (floats)

- Dataframe Dimensions: 210 rows x 8 columns (Last column is depecits the type of wheat *which is removed from cluster analysis*)
![screenshot 1](https://user-images.githubusercontent.com/33742913/35468400-b8e7edfe-02d1-11e8-824f-895db15e93b4.PNG)

The examined group comprised kernels belonging to three different varieties of wheat: Kama, Rosa and Canadian, 70 elements each, randomly selected for the experiment. 

To construct the data, seven geometric parameters of wheat kernels were measured: 
1. area A, 
2. perimeter P, 
3. compactness C = 4*pi*A/P^2, 
4. length of kernel, 
5. width of kernel, 
6. asymmetry coefficient 
7. length of kernel groove. 
All of these parameters were real-valued continuous.

High quality visualization of the internal kernel structure was detected using a soft X-ray technique. It is non-destructive and considerably cheaper than other more sophisticated imaging techniques like scanning microscopy or laser technology. The images were recorded on 13x18 cm X-ray KODAK plates. Studies were conducted using combine harvested wheat grain originating from experimental fields, explored at the Institute of Agrophysics of the Polish Academy of Sciences in Lublin. 

The data set can be used for the tasks of classification and cluster analysis.

**Summary statistics of the data**
![summary](https://user-images.githubusercontent.com/33742913/35468455-115edfd2-02d3-11e8-94c0-10cc2b9ff19e.PNG)


## Proposed Solution

The proposed is to compare the K-Means Clustering machine learning algorithms and to identify if this is one the best at identifying the variety of wheat from its geometric properties.

The data was downloaded from the UCI machine learning repository and loaded into Juypter for analysis.

The data was visualised and plotted in R. We use the seeds data set to demonstrate cluster analysis in R. The examined group comprised kernels belonging to three different varieties of wheat: Kama, Rosa and Canadian, 70 elements each.
The visualisations show that the data does fall into a number of distinct clusters. These distributions suggest that the data should lend itself to clustering and classification.

**K- Means Clustering**
The main objective in cluster analysis is to group objects that are similar in one cluster and separate objects that are dissimilar by assigning them to different clusters. One of the most popular clustering methods is K-Means clustering algorithm. It classifies object to a pre-defined number of clusters, which is given by the user (assume K clusters). The idea is to choose random cluster centres, one for each cluster. These centres are preferred to be as far as possible from each other. 
K-Means clustering is a process whereby n observations are assigned to one of K clusters based on the distance to the mean of the cluster. The clustering process is initialised by random selection of points from the data set. The nearest distance is derived by the within cluster sum of squares. 
The K-Means clustering algorithm used for the analysis was loaded from the NbClust library.  The data was prepared by scaling so that all of the attributes fall within a similar range of values. The scaled data is then passed through the K-Means clustering algorithm to find the optimum number of clusters. A plot of the within groups sum of squares was produced suggesting that the optimum number of clusters was three.

![naive](https://user-images.githubusercontent.com/33742913/35469164-ae95d9d4-02e4-11e8-9d3f-d403c94feae5.PNG)

![k cluster](https://user-images.githubusercontent.com/33742913/35468706-b3995bba-02d8-11e8-8454-cfbcd0cb00cd.PNG)

![cluster over attributes](https://user-images.githubusercontent.com/33742913/35468705-b37f0ed6-02d8-11e8-9ef8-df0aa46d09b1.PNG)

The K-Means was able to successfully identify three naturally occurring classes without using the label attribute. This fits with the label attribute and what we know about the data. The K-Means algorithm successfully picked out 3 clusters without using the target attribute.  When the target attribute is compared to the predictive cluster it can be seen that the clustering process is very good.  

**Model based Cluster Analysis - Gaussian Mixture Model**
Few more option for cluster Analysis are Gaussian Mixture Model, Cluster Dendrogram


![gussain 1](https://user-images.githubusercontent.com/33742913/35469228-eeb4d4a6-02e5-11e8-83d2-49166e6133bc.PNG)

![gussain 2](https://user-images.githubusercontent.com/33742913/35469229-eed0c29c-02e5-11e8-8ef6-41bf5c1ddab2.PNG)

![gussain 3](https://user-images.githubusercontent.com/33742913/35469230-eeefacd4-02e5-11e8-84f3-1eaa38f79867.PNG)

![gussain 4](https://user-images.githubusercontent.com/33742913/35469231-ef0e8a64-02e5-11e8-9a52-d6dd7a170608.PNG)


## Benchmark Model

A naive model would be average of each col (factor of seeds) & analyse the variance between each type of seed.

![untitled](https://user-images.githubusercontent.com/33742913/35469536-45465d12-02eb-11e8-917f-8ab4b15e8931.png)

## Performance Metric 
Given that this is a clustering task, we can measure the success of our model using Silhouette Score or Dunn Index

![performance 1](https://user-images.githubusercontent.com/33742913/35469113-17aae330-02e3-11e8-9dbc-c9956d715601.PNG)

![performance 2](https://user-images.githubusercontent.com/33742913/35469114-17c9c034-02e3-11e8-8324-8de23fc010c3.PNG)

## Conclusion

K-Means algorithms performed very well on this data set and were able to identify the variety of wheat by the geometric properties of the seed kernels.  The K-Means was able to successfully identify three naturally occurring classes without using the label attribute. This fits with the label attribute and what we know about the data.  

This experiment also shows that it would be possible to use the K-Means algorithm to generate a set of classes  from data that doesn’t have a classification label attribute.
# Project-Seeds
