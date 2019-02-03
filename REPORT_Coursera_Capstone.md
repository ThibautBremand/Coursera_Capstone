# Coursera_Capstone
Capstone project : Battle of the Neighbourhoods

## Clustering Neighbourhoods by demographic data
### Use case : I want to find the best area to open my new restaurant  

#### 1. Introduction

*1.1 - Cluster Toronto neighbourhoods using demographic data*  

When you look for the best place to open a new restaurant in a city like Toronto, **you have to gauge people's taste in each neighbourhood of the city**. You will then know in what neighbourhood of the city people will likely come and spend money in your restaurant.

A good way to gauge people's taste in a specific area is to **look into the demographic data of this area**. For example, areas with a mojority of chinese people would be good for chinese restaurants, and areas with a mojority of italian people would be good for opening an italian restaurant, etc.  

With this kind of demographic data associated with different neighbourhood of Toronto, we can cluster neighbourhoods by demographic data. Thus, we will be able to distinguish the areas where a lot of chinese people live, the areas where a lot of italian people live, and so on, based on the clustering.  

*1.2 - Find the best neighbourhoods within a cluster to open the restaurant*  

Once the neighbourhoods have been categorised into clusters, and you've got a list of neighbourhoods where people living there would likely want to eat in the restaurant you want to open, **you need to find out in which neighbourhoods there is less competition**. It means that you have to find out **what neighbourhoods contain the lowest number of existing restaurants of the same type** as the one you want to open.  

In order to count the number of existing restaurants of the same type in a neighbourhood, we perform a **FoursquareAPI explore query**. Like that, we obtain the list of venues of each neighbourhood, and we can count the number of restaurants of each type.   

#### 2.Data  

The list of neighbourhoods, and the demographic data associated to each neighbourhood, has been made available by the city of Toronto here :  
- https://www.toronto.ca/ext/open_data/catalog/data_set_files/2016_neighbourhood_profiles.csv  
