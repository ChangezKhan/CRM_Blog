---
title:  "Recommendation System for Grocery Vendors"
date:   2020-05-23 23:04:23
categories: [Machine Learning]
tags: [Clustering]
---

Hello all,

Here we will see how to cluster the Neighborhoods of New York City on basis of no. of restaurants and recommend the neighbourhoods/borough to grocery vendors. 

## Introduction

First we'll get to know more about the New York City. New York City (NYC), often called the simply New York (NY), is the most populous city in the United States. With an estimated 2018 population of 8,398,748 distributed over about 302.6 square miles (784 km2), New York is also the most densely populated major city in the United States. Located at the southern tip of the U.S. state of New York, the city is the center of the New York metropolitan area, the largest metropolitan area in the world by urban landmass. With almost 20 million people in its metropolitan statistical area and approximately 23 million in its combined statistical area, it is one of the world's most populous megacities. New York City has been described as the cultural, financial, and media capital of the world, significantly influencing commerce, entertainment, research, technology, education, politics, tourism, art, fashion, and sports. 

Situated on one of the world's largest natural harbors, New York City is composed of five boroughs, each of which is a county of the State of New York. The city and its metropolitan area constitute the premier gateway for legal immigration to the United States. As many as 800 languages are spoken in New York, making it the most linguistically diverse city in the world. New York is home to more than 3.2
million residents born outside the United States, the largest foreign-born population of any city in the world as of 2016.

## Problem Background

Above introduction gives a vague idea that people from various parts of the world is living in the city. Hence the diversity in the food industry is also required. As it is highly developed city so cost of doing business is also one of the highest. Thus, any new business venture needs to be analyzed carefully. The insights derived from analysis will give good understanding of the business environment which help in strategically targeting the market. This will help in reduction of risk. And the Return on Investment will be reasonable.

## Problem Description

In 2019, there were 27,043 restaurants in the city, up from 24,865 in 2017. New York City's food culture includes an array of international cuisines influenced by the city's immigrant history. 

Central and Eastern European immigrants, especially Jewish immigrants from those regions, brought bagels, cheesecake, hot dogs, knishes, and delicatessens (or delis) to the city. Italian immigrants brought New York-style pizza and Italian cuisine into the city, while Jewish immigrants and Irish immigrants brought pastrami and corned beef, respectively. Chinese and other Asian restaurants, sandwich joints, trattorias, diners, and coffeehouses are ubiquitous throughout the city. Some 4,000 mobile food vendors licensed by the city, many immigrant-owned, have made Middle Eastern foods such as falafel and kebabs.

So this gives an idea that to supply groceries to all these restaurants, it needs to be studied carefully so one can maximizes its services to variety of the restaurants in less efforts.

So here in this case, we are going to study following problem:
  * If you are a groceries supplier, then which part of the city will be better in terms of providing services as well in earning higher profits?

## Data Acquisition

For this case study, we will be using the below datasets:
  * New York City has a total of 5 boroughs and 306 neighborhoods. In order to segment the neighborhoods and explore them, we will
essentially need a dataset that contains the 5 boroughs and the neighborhoods that exist in each borough as well as the latitude and
longitude coordinates of each neighborhood. Link to the dataset is: https://geo.nyu.edu/catalog/nyu_2451_34572
  * Along with the above dataset, we will utilizing New York City's geographical coordinates with the Foursquare API which will help us
provide details regarding all the restaurants in the area. URL of the Foursquare developer portal: URL of the Foursquare developer portal: https://developer.foursquare.com/

## Data Pre-processing

First we will download the New York City’s 5 boroughs and 306 Neighborhood dataset which contains the latitude and the longitude of each
neighborhood. This data is in JSON format. We will convert this data into pandas dataframe. After that, we’ll utilize the Foursquare API to fetch the 100 restaurants in each neighborhood area within the 500 meters. Once we get fetch data using the Foursquare API, the resultant dataset will look like this:
![dataset_1](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/dataset_1.JPG)

## Data Exploration

Now, we have acquired the data we want, we’ll try to plot the map using the latitude and longitude of all the venues of all the neighborhoods with respect to the Borough using the Folium library. 
![map_1](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/neighborhood-map.png)

## Feature Selection

To accomplish our goal, we’ll need total no. of venues/restaurant against each neighborhood. For this, we’ll take count of the all the Venues respective to the neighborhood. And this will be our Final dataset which we will use to train our cluster model on it.
![dataset_2](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/dataset_2.JPG)

## Clustering Algorithm

To accomplish our goal, we are going to utilize k-means clustering algorithm to cluster the neighborhoods. But first we will utilize the elbow method to get the ideal number of cluster number. And the result looks like this:
![elbow_curve](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/elbow_curve.png)

When we graph the plot, we see that the graph levels off slowly after 3 clusters. This implies that addition of more clusters will not help us that much. Hence, we'll be clustering our data into 3 partitions.

After training the k-means model to cluster our dataset into 3 partitions, we get the result which looks like this:
![dataset_3](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/dataset_3.JPG)

## Analyzing our Clusters

First we will see how the data spread in each cluster is by getting average no. of venues/restaurant respective to the clusters. And the result looks like this:
![cluster_mean](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/cluster_mean.png)

At this point we can pretty much conclude that the third cluster which is the cluster no. 2 is the cluster of neighborhoods which has on average more than 40 numbers of restaurants and these neighborhoods any grocery vendors should target to build/expand the business.

Now, we’ll try to analyze the frequency of the venues/restaurants in each boroughs with respect to the clusters.
![clusterwise_borough_dist](https://raw.githubusercontent.com/ChangezKhan/crm_blog/master/images/clusterwise_borough_dist.png)

Now, if we analyze carefully, we will find out that the Manhattan is the only Borough which all neighborhoods has almost 40 venues/restaurants and it features only in the Third cluster which is a cluster no. 2. And this cluster no. 2 is the cluster of all neighborhoods which has on average more than 40 venues/restaurants.

## Conclusions

As mentioned in our Problem statement, our goal is to find the cluster of neighborhoods which has large no. of venues/restaurants which will be used to recommend any grocery vendors to start/expand their business. Also the above study using the clustering algorithm pretty much accomplish our goal by suggesting the Manhattan borough of New York City has large no. of venues/restaurants. Along with this, in each borough there are many neighborhoods which has large no. of venues/restaurants

## Future Directions

Using the above study, we can further go deep into what kind of restaurants each neighborhood has and this feature has any relationship with the diverse population of the New York City. Also, we can provide more analysis on If one wants to open a new restaurants of a particular type, which part of the city will be less competitive and highly profitable.

Also, we can provide analysis on what part of the city anyone can start a new restaurants and what kind of competition it will have from the other restaurants. 

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
