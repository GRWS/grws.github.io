---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title:  Home
---

# **After Job Offer, Choosing a Neighborhood in New York City**

## Table of Contents
1. [Introduction](#introduction)

2. [Data](#Data)

3. [Methodology](#Methodology)

4. [Results](#Results)

5. [Further Discussion](#Discussion)

6. [Conclussion](#Conclussion)

## 1. Introduction <a name="introduction"></a>

Moving to a different city comes with a number of challenges, and one of the biggest ones is to find the right place to live.  The choice of which neighborhood to live, within the new city, comes with a number of important questions. A few of the ones that come to mind are: 
* How much it will housing cost? 
* How much time the daily commute will take? 
* What kind of venues are near it? 

Regarding such questions, this project aims to answer them, at a general level, given two specific premises.  First, having found a new job in the financial district, located in lower Manhattan, and second, planning to live within one of the five New York City boroughs.
Based upon the assumptions given, this project compares average rent prices for different neighborhoods in Manhattan, Queens,  Brooklyn, the Bronx and Staten Island, the times that it takes to commute from them during rush hour, along with the most popular venues in them.


## 2. Data <a name="Data"></a>

To complete this project, it was necessary to gather data regarding rent, commuting times, and most popular venues for each of the neighborhoods in question.  While some of the data was readily available, the commuting times were collected individually from each neighborhood using google maps.  The specific data sources are listed below.

* Average rental data per neighborhood is available at:
https://streeteasy.com/blog/data-dashboard/

* The latitude and longitude for the neighborhoods across all five boroughs is available in different file formats, i.e. Derived Shapefile, KMZ and GeoJSON from:
https://geo.nyu.edu/catalog/nyu_2451_34572

* The commute times were collected from Google Maps:
https://www.google.com/maps/

* Lastly, the Foursquare API was used to find information about the venues location and their popularity among Foursquare users:
https://developer.foursquare.com/docs/api/venues/explore

## 3. Methodology <a name="Methodology"></a>
### 3.1 Data Cleaning
The choice of making the Wall Street financial district the target location for place to work, and therefore to commute to and from, was based on a report published by the New York City government which states that both lower and midtown Manhattan have the highest job density of the greater New York Metropolitan area, comprised by the 5 New York City boroughs, as well as northern New Jersey, Long Island, Southwest Connecticut, and the Hudson Valley.  The report is available here:

[The Geography of Jobs: NYC Metro Region Econnomic Snapshot (July 2018)]
<https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=9&cad=rja&uact=8&ved=2ahUKEwi295LHwZLkAhULsZ4KHQESBwIQFjAIegQIARAC&url=https://www1.nyc.gov/assets/planning/download/pdf/about/dcp-priorities/data-expertise/nyc-geography-jobs-0718.pdf&usg=AOvVaw3z8DN3u6trL_TVPZjJDR9L>

Also, according to a study performed by the Center for Urban Future in 2014, in spite that New Yorkers are likely to work on their home borough, Manhattan is still the city's employment center.
<https://nycfuture.org/data/fast-city-slow-commute>

Due to the wide popularity and accessibility of the subway, and that surface speeds have decreased over time, particulartly in Manhattan, this project uses the subway as the most consistent and reliable means of commuting. A link to the Mobility Report, from the NYC Department of Transportation discussing these findings can found here:
[Mobility ReportJune 2018 - NYC.gov]
<http://www.nyc.gov/html/dot/downloads/pdf/mobility-report-2018-print.pdf>

Regarding the commute times, they are several online tools which are able to show, on real-time, the time it takes to commute from different city areas, however their accuracy proved to be poor when compared to real-time data from google maps.  It is possible, the these tools were relying on information provided by all kinds of commuting means used in New York City, which include walking, driving or hiring a taxi cab or riding sharing service, biking, bus, subway and, in some cases, ferries. One of such tools can be found via the following link:
<https://www.mapnificent.net/newyork/#12/40.7290/-73.9980/900/40.7290/-73.9980/900/40.8117/-74.0211>

Since the commute information from each individual neighborhood, during rush hour, wasn't readily readily available, it was necessary to collect commuting times individually from Google Maps, so that a comprehensive time, as well as accurate, data table could be created.  The times were calculated based upon the following:

```python
Average Commute Time = (Time Morning Commute + Time Evening Commute) / 2
```


### 3.2 Feature Selection


Depending upon the individual user some features could be more important than others.  As expected, compromises may have to be made in order to find a suitable choice of housing. A shorter commute might mean a significantly higher rent, or fewer desirable venues near the chosen location. With that in mind, different classifications were made individually for each of the selected features.  The first of which dealt with rental cost at all the different neighborhoods.  As the graph below shows, the average rent prices has a rent price ranging from `$1,500.00` per month in Bedford Park Neighborhood park of the Bronx to `$7,400.00` per month in Manhattan's Central Park South.



![nyc_rent_prices](https://user-images.githubusercontent.com/51925289/64658985-63b51600-d3ee-11e9-83f4-2f3508ab9896.png)


Also, it is worth noting that the biggest limiting factor for the whole data set was the number of neighborhoods for which average rental data was available.  Originally nearly two hundred neighborhoods, across all five boroughs, were considered, but only recent and reliable data, the latest being from April of 2019, was available for 103 of them, which are listed on the plot above. As shown, the data was incomplete for any neighborhoods in Long Island; some had rental data and venue data while some did not.  It was decided to exclude those neighborhoods altogether, so that a fair assessment could be made.


### 3.3 Selected Features Maps
To better display each neighborhood location, along with their corresponding average rental price, commute times and number of venues, the Python Folium library was used to generate three individual maps. The individual neighborhood locations are shown on the map by using the latitude and longitude information from the GEOjson file mentioned earlier in the Data section.  The difference between the overall data values gathered is displayed both by the color and size of the map markers, with larger circles denoting higher values.  To see the interactive version of the maps, please follow the links provided for each of them below their respective pictures. Clicking on the circles displays the individual neighborhood name, along with the numerical value related to that map related feature.

As the map below shows,  is clear that, with some exceptions, the neighborhoods closer to lower Manhattan's financial district command higher average rental prices, than other locations within New York City. 

![nyc_rent_prices](https://user-images.githubusercontent.com/51925289/64983772-27623980-d876-11e9-93c2-ad4893a043c2.JPG)

The link to the interactive map pictured above is located at <https://grws.github.io/NYC_rents_map>


Next, the map below shows the commute times from the different neighborhoods to the financial district.  As it can be expected, with a few exceptions, the commute times are shorter from Manhattan neighborhoods than the ones from other boroughs.

![nyc_commute_pic](https://user-images.githubusercontent.com/51925289/64987455-0ac9ff80-d87e-11e9-81ff-d027e429dbd6.JPG)

The link to the interactive map pictured above is located at <https://grws.github.io/NYC_commute>



Using the Foursquare location database Application Program Interface (API), it was possible to retrieve the information about the most popular places in each of the neighborhoods under consideration.  The New York City metropolitan area enjoys a great variety and number of popular venues; however, when it comes to individual neighborhoods, the data showed that there is a significant variation on the number of popular venues nearby.  As a result, it can be inferred that a larger number of popular venues indicates a more desirable neighborhood, since there a larger variety of things to do closer to a prospective rental choice.  For simplicity purposes, the number of venues per neighborhood was capped at a maximum of 100.  As the map shows, some of the neighborhoods have very few popular venues.

![nyc_venue_count_pic](https://user-images.githubusercontent.com/51925289/64987791-cf7c0080-d87e-11e9-8e5a-911c96741173.JPG)

The link to the interactive map pictured above is located at <https://grws.github.io/NYC_venue_count>

A table displaying the seven most common venues per neighborhood can be seen by using the Venue Table link, located at header atop this page, or here: <https://grws.github.io/Venues/>



## 4. Results <a name="Results"></a>
The following table shows the averages for each of the features under consideration. It is easy to see from it, that Manhattan leads way on higher average rent prices, shorter commute times and largest number of venues per neighborhood, followed by Brooklyn, Queens and the Bronx.

|Borough|Average Rent Price|Average Commute Time in Minutes|Average Number of Venues per Neighborhood|
|--- |--- |--- |--- |
|Manhattan|$3,650.10|27.52|80.48|
|Brooklyn|$2,506.65|34.84|49.29|
|Queens|2,086.22|56.89|42.59|
|Bronx|1,829.59|61.83|27.82|



Now adding some python code and trying to see if it would show the map!
{% highlight python %}
import folium
print('Folium installed and imported!')
m = folium.Map(location=[45.5236, -122.6750])

m
{% endhighlight %}

What happened?
