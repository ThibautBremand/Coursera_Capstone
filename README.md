# Coursera_Capstone
IBM Data Science Professional Certificate - Capstone project : Battle of the Neighbourhoods.  

This project is related to the **IBM Data Science Professional Certificate** :  
https://www.coursera.org/specializations/ibm-data-science-professional-certificate  

**Note :** If you want to see all the Folium maps in this notebook, you can visualise the notebook through **nbviewer** :  
https://nbviewer.jupyter.org/github/ThibautBremand/Coursera_Capstone/blob/master/Toronto_Neighbourhood_Clustering.ipynb   

# Toronto's Neighbourhoods Clustering using K-means.  
We apply a **K-Means algorithm** onto the list of all Toronto's neighbourhoods, in order to visualise differences between neighbourhoods within the city of Toronto.  

## 1/ Clustering Neighbourhoods by venues categories
### Use case : I want to find the best neighbourhood to live in  

**Context :** When you want to live in a city, you may be looking for a neighbourhood regarding its types of venues. 
- For example, **if you want to go to the park everyday, you will be likely to live in a neighbourhood that containts a lot of parks**. If you love coffee shops, you may want to live in a neighbourhood that containts a lot of coffee shops.  
- If you need to relocate, because your job has changed, you may be looking for a **similar neighbourhood with the same types of venues**, nearer your new job's place. If so, this type of clustering will help you finding out these similar neighbourhoods, because you will see each cluster represented on a map.  

The clustering is made using the types of venues that constitute each neighbourdhood. For example, neighbourhoods with a lot of parks around are most likely to be categorised into the same cluster.  

**Method :** 
- The list of neighbourhoods is scrapped from Wikipedia, using the library **BeautifulSoup**.  
- Each neighbourhood's coordinates are retrieved using **Geocoder**.
- The list of venues for each neighbourhood are retrieved from **FoursquareAPI**.  
- The clustering is done using a **K-means algorithm**.
- The neighbourhoods are displayed on a map using **Folium**, each colored for each cluster.  

With this clustering method, we can see neighbourhoods that are similar using their most common types of venues.  

## 2/ Clustering Neighbourhoods by demographic data
### Use case : I want to find the best area to open my new restaurant  

**Context :** This time, we will cluster the city of Toronto by demographic data, and especially by Ethnic origins, in order to find the best places to open a new restaurant.  
- If, for example, **you want to open a new chinese restaurant in Toronto, you will be looking for areas where a lot of people of Chinese ethnic origins live**, so you will be sure that people will be interested by your restaurant nearby.  
- Once you found out the areas with a lot of people with chinese ethnic origins, we assume that **you will be looking for the areas with the lower number of already existing chinese restaurants**. Thus, there will be less competition.  

The clustering is made using the demographic data of Toronto, made available by the city of Toronto here :  
- https://www.toronto.ca/ext/open_data/catalog/data_set_files/2016_neighbourhood_profiles.csv

This dataset gives demographic data by **city areas**, which differ a bit from the neighbourhoods we scraped from Wikipedia. That's why we will be talking about city areas and not neighbourhoods in this notebook.  

**Method :** :
- The list of city areas is retrieved from the **Toronto Open Data CSV file**.
- Each city area's coordinated are retrieved using **Geocoder**.
- The demographic data for each city area also comes from the **Toronto Open Data CSV file**.
- The clustering is done using a **K-Means algorithm**.
- For each interesting cluster (for example, if we want to open a Chinese restaurant, we will take clusters with a lot of Chinese people living in), we will count the number of existing restaurants by area, using **FoursquareAPI**.
- We assume that the areas with the lowest number of existing restaurants of the same category within these clusters are the top spots to open the restaurant.
- We display the top spots on a map using **Folium**.
