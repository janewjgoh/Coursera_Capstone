The Battle of Neighborhoods in Shanghai
Author: Jane W.J. Goh
Date: 01 November 2020

Introduction

After moving across 8 different cities(/towns) in different countries in the past 20 years, I have come to appreciate a neighborhood that has local flavor, convenient access to healthy living, as well as foreign touch that reminds me of home- Los Angeles. However, with every move, the search for a good base that meets every criterion remains difficult, especially so when all one has is Google maps and websites targeting expats and charging agency fees- is it a fair price or overcharged? Is this a foreigner-friendly neighborhood? Is it convenient to all the daily necessities? Moving to a new city can be a daunting experience, especially when you 1. don't know anyone, 2. are not familiar with the landscape, and 3. don't speak the language. 

Shanghai is home to 200,000 expats, the largest expat population in China mainland. With housing information available largely in Chinese, some work can be done to close the information asymmetry. This project explores and clusters the neighborhoods in Shanghai in order to find a suitable community for a new expat in town. 

There are 3 parts to the project:
1. Importing and cleaning the Shanghai neighborhoods data
2. Calling Foursquare API to find each neighborhood's characteristics- by most common venue
3. Using k-means to cluster the neighborhoods & analysis

Data

Neighborhood here is defined as within 400 meter/ 5-minute walking distance of a metro station- the main form of transport between home and office. Neighborhood characteristics is defined by the type of venues available from the 400 meter/ 5-minute walking distance of the metro station.

This notebook makes use of two main sources of data 1. CSV file containing Shanghai’s 423 metro stations in English and Chinese names, locations, latitude, longitude data and 2. Foursquare API which provides venues data for each latitude, longitude data points. 

The ShanghaiMRTLatLng.csv file data is sourced from a 2016 data available on https://blog.csdn.net/a364572/article/details/50483568. However, the data source is available in mandarin and not up to date in 2020 as there have been 60+ new stations added since then, found from wikitable search from https://en.wikipedia.org/wiki/List_of_Shanghai_Metro_stations. I extracted the full list of metro stations from wikitables, merged the latitude longitude data with the 2016 files, and updated manually the missing data points and the data is now available as csv in the repository. 

Methodology

In preparing the Shanghai neighborhoods data, duplicated station names were removed. Reason being one station might be an interchange of several metro lines, all the duplicated stations were dropped and keep only the first occurrence because the same station names are unlikely to be too far away from each other. 

After merging the data from Shanghai neighborhoods and Foursquare data, I realized that there are insufficient data in a lot of locations, so I have removed them from consideration in the notebook steps 2.2.5 and 2.2.6. 

Next, self-defined functions are used to find the neighborhoods’ characteristics, and this is the resulting look. 

Now, It may be good enough to know what is popular in each neighborhood, however, we’ll take it a step further and find which neighborhoods are more similar in spirit through clustering analysis.

In order to find similar neighborhoods, K-Means is chosen to learn from the data and cluster the neighborhoods unsupervised. K-Means is chosen as it is able to find similar and dissimilar groups in unlabeled data, and it is an algorithm that is accessible to beginners.

In selecting K, I have opted for 5 as I deemed the elbow method’s 2 is insufficient to make a more detailed segregation amongst the neighborhoods. 

Results

Upon examining the resulting clusters, one can infer a characteristic of different neighborhoods in town:

Cluster 1: People's square station is filled with variety of Asian cuisine restaurants, hotels, and karaoke bar- indicating that this might be a very bustling place, suitable for someone who prefers a busy environment with easy access to food and entertainment

Cluster 2: Xinzha Road and Shangcheng Road stations are concentrated in largely Asian/some Western restaurants and cafes, hotels and b&b's, and shopping (sports & clothes)- an indication that it could be an area that is convenient for tourist access.

Cluster 3: Xujiahui, Lujiazhui and Huamu Road stations are first and foremost about coffee shops, followed by a mix of Asian/Western restaurants, and access to shopping malls/ convenience stores/ supermarket, these are indications of the convenient city lifestyle

Cluster 4: South Huangpi Road and Jian'an Temple stations are the first clusters where we see gym and park making it to the top 10. Along with a mix of Asian/Western restaurants and cocktail bars, this cluster looks like a good base for work/life balance.

Cluster 5: East Nanjing Road and Shanghai Library stations are defined by its lounge/bistro/deli, largely Western restaurants. And the art gallery and jazz club? This cluster looks like one fine lifestyle neighborhood.

Discussion

This project could be further improved with the following:

In part 1: Introduce a web crawler and more comprehensive data cleaning codes. 
In part 1, 2: Can include other potential data sources such as average property price, surround building types, and residential demographic to make neighborhood characteristics identification even more meaningful. 
In part 3: Instead of K-Means, maybe can explore DBSCAN density-based clustering. 

Conclusion

We have made a headway into exploring of different neighborhoods in Shanghai, a different cluster for everyone with different lifestyles. For people who are looking to a new place, hope you find a place to call home. For my fellow classmates, Happy Learning! 
