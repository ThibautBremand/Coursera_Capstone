# Coursera_Capstone
IBM Data Science Professional Certificate - Capstone project : Battle of the Neighbourhoods.  

This project is related to the **IBM Data Science Professional Certificate** :  
https://www.coursera.org/specializations/ibm-data-science-professional-certificate  

**Note :** If you want to see all the Folium maps in this notebook, you can visualise the notebook through **nbviewer** :  
https://nbviewer.jupyter.org.  
Just paste the Github notebook link into nbviewer.  

## Toronto's Neighbourhoods Clustering using K-means. 
The **Toronto_Neighbourhood_Clustering** notebook applies a k-means algorithm onto the list of all Toronto's neighbourhoods, in order to visualise differences between neighbourhoods within the city of Toronto.  

The clustering is made of the types of venues that constitute each neighbourdhood. For example, neighbourhoods with a lot of parks around are most likely to be categorised into the same cluster.  

- The list of neighbourhoods is scrapped from Wikipedia, using the library **BeautifulSoup**.  
- Each neighbourhood's coordinates are retrieved using **Geocoder**.
- The list of venues for each neighbourhood are retrieved from **FoursquareAPI**.  
- The clustering is done using a **K-means algorithm**.
- The neighbourhoods are displayed on a map using **Folium**, each colored for each cluster.  
