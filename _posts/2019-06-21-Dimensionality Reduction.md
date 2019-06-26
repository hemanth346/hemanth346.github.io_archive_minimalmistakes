---
title  : Dimensionality Reduction techniques
date : 2019-06-21
---
Before jumping into techiques, first lets understand what is dimensionality reduction and why do we need techniques like PCA, t-SNE, MDS(Multi Dimensional Scaling), Sammon mapping or any other techniques


## Dimensionality Reduciton

Two common reasons why we would want to reduce the dimensions of given data.

1. Visualization purposes
2. The Curse of Dimensionality

### 1. Visualization

We, humans, are yet unable to visualize data in more than 3D. For data that is in higher dimensions we often try to plot muliple plots (eg. pair plots) between the features and try to make sense of how the data behaves. But this is exhaustive and doesn't work for data with dimensions greater than 6-7, which is more often the case in Machine learning. 

Dimensionality reduction techniques help in projecting data to 2D or 3D, so that we can be able to visualize data in 2D/3D spaces.

### 2. The Curse of Dimensionality

In essence, what it means is that for the same number of datapoints in training data - as the number of dimensions increases, beyond a point, the performace of the model decreases. We can counter this by increasing the amount of training data, but we also increase the processing power we need to analyze the data. 

*There is a very good explination about curse of dimensionality [here] [1], please do read it.*

To avoid the 'Curse of Dimensionality', there are 2 methods

##### 1. Feature selection

	***Select*** a subset of original features manually, usually based on the domain expertise

##### 2. Feature extraction (Feature Projection)

	 ***Creates*** new features by projecting the data in the high-dimensional space to a space of fewer dimensions. 
	Dimensionality reduction techniques are used here.

## Dimensionality Reduciton Techiques


As discussed, dimensionality reduction can be achieved by either feature selection or feature extraction. 

	In feature selection we only keep subset of original features from the dataset

	In feature extraction we create new features, using original features. 

There are multiple algorithms/techniques developed. This [blog] [2] post talks about some of them breifly along with the python code. 



*To summarize Dimensionality reduction helps in better human visualization of the data and in reduced computational costs*


***In next series of posts, I'll be writing about PCA and t-SNE***


[1]: https://towardsdatascience.com/curse-of-dimensionality-2092410f3d27 "Curse of Dimensionality, by Badreesh Shetty - Towards Data Science"
[2]: https://www.analyticsvidhya.com/blog/2018/08/dimensionality-reduction-techniques-python/ "12 Dimensionality Reduction Techniques - Analytics Vidhya"
