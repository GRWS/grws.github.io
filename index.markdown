---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title:  Home
---

# **After Job Offer, Choosing a Neighborhood in New York City**
## **Capstone Project (Week 1)**

## Table of Contents
1. [Introduction: Business Problem](#introduction)

2. [Data](#Data)

## 1. Introduction: Business Problem <a name="introduction"></a>

Moving to a different city comes with a number of challenges, and one of the biggest ones is to find the right place to live.  The choice of which neighborhood to live, within the new city, comes with a number of important questions. A few of the ones that come to mind are: 
* How much it will housing cost? 
* How much time the daily commute will take? 
* What kind of venues are near it?.  

Regarding such questions, this project aims to answer them, at a general level, given two specific premises. First, having found a new job in the financial district, located in lower Manhattan, and second, planning to live within one of the five New York City boroughs.
Based upon the assumptions given, this project compares average rent prices for different neighborhoods in Manhattan, Queens,  Brooklyn, the Bronx and Staten Island, the times that it takes to commute from them during rush hour, along with the most popular venues in them.


## 2. Data <a name="Data"></a>

To complete this project, it was necessary to gather data regarding rent, commuting times, and most popular venues for each of the neighborhoods in question.  While some of the data was readily available, the commuting times were collected individually from each neighborhood using google maps.  The data sources are listed below.

* Average rental data per neighborhood is available at:
https://streeteasy.com/blog/data-dashboard/

* The latitude and longitude for the neighborhoods across all five boroughs is available in different file formats, i.e. Derived Shapefile, KMZ and GeoJSON from:
https://geo.nyu.edu/catalog/nyu_2451_34572

* The commute times were collected from Google Maps:
https://www.google.com/maps/

* Lastly, the Foursquare API was used to find information about the venues location and their popularity among Foursquare users:
https://developer.foursquare.com/docs/api/venues/explore

{% highlight python %}
## sorting dataframe in ascending order to generate plot
df_ct = df_ct.sort_values('AvgRent')

## Checking types for the merged dataframe
df_ct.dtypes

# Changing AvgRent column contents from float to int 
df_ct['AvgRent'] = df_ct['AvgRent'].apply(np.int64)

## Dropping extra column and resetting index for the newly sorted dataframe
df_ct = df_ct.drop(['variable'], axis =1).reset_index(drop=True)
df_ct.head()
{% endhighlight %}

Index	Commute Time in Minutes 	Neighborhood 	Borough 	Latitude 	Longitude 	AvgRent
0 	54 	Bedford Park 	Bronx 	40.870185 	-73.885512 	1550
1 	58 	Norwood 	Bronx 	40.877224 	-73.879391 	1598
2 	80 	Williamsbridge 	Bronx 	40.881039 	-73.857446 	1600
3 	58 	Morris Heights 	Bronx 	40.847898 	-73.919672 	1650
4 	54 	Woodlawn 	Bronx 	40.898273 	-73.867315 	1650

The figure below shows the average rent prices, from lowest to highest, across different neighborhoods in New York City.
![nyc_rent_prices](https://user-images.githubusercontent.com/51925289/64658985-63b51600-d3ee-11e9-83f4-2f3508ab9896.png)


Adding more things to this file.

We'll see if it makes a difference or not. I'd like to find out!

Check out the NYC Commute map I created:

![NYC_commute_pic2](https://user-images.githubusercontent.com/51925289/64222030-a70a0480-ce83-11e9-910d-61fa7f83bc39.JPG)

The link to image above is here [NYC Commute Map][NYC_commute]

[NYC_commute]: /NYC_commute


Now adding some python code and trying to see if it would show the map!
{% highlight python %}
import folium
print('Folium installed and imported!')
m = folium.Map(location=[45.5236, -122.6750])

m
{% endhighlight %}

What happened?
