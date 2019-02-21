# Coursera_Capstone
Capstone project : Battle of the Neighbourhoods

## Clustering Neighbourhoods by demographic data
### Use case : I want to find the best area to open my new restaurant  

### 1. Introduction

This project is about **finding the best neighbourhoods in the city of Toronto to open a new restaurant of a specific type** (for example : chinese, or italian restaurant).  
**This project would interest anyone which wants to open a new restaurant in the city of Toronto, and seeks the best neighbourhoods** where the habitants would likely eat in this kind of restaurant, and where the competition is limited (e.g. there is a a reasonable number of existing restaurants of the same type in the neighbourhood).

#### 1.1 - Cluster Toronto neighbourhoods using demographic data 

When we look for the best place to open a new restaurant in a city like Toronto, **we have to gauge people's taste in each neighbourhood of the city**. We will then know in what neighbourhood of the city people will likely come and spend money in our new restaurant.

A good way to gauge people's taste in a specific area is to **look into the demographic data of this area**. For example, areas with a majority of chinese people would be good for chinese restaurants, and areas with a majority of italian people would be good for opening an italian restaurant, etc.  

With this kind of demographic data associated with different neighbourhoods of Toronto, **we can cluster neighbourhoods by demographic data**. Thus, we will be able to distinguish the areas where a lot of chinese people live, the areas where a lot of italian people live, and so on, based on the clustering.  

#### 1.2 - Find the best neighbourhoods within a cluster to open the restaurant

Once the neighbourhoods have been categorised into clusters, and we've got a list of neighbourhoods where people living there would likely want to eat in the restaurant we want to open, **we need to find out in which neighbourhoods there is less competition**. It means that we have to find out **what neighbourhoods contain the lowest number of existing restaurants of the same type** as the one we want to open.  

In order to count the number of existing restaurants of the same type in a neighbourhood, we perform a **FoursquareAPI explore query**. Like that, we obtain the list of venues of each neighbourhood, and we can count the number of restaurants of each type.   

### 2.Data  

#### 2.1 - Demographic data from the City of Toronto's open data

The list of neighbourhoods, and the demographic data associated to each neighbourhood, has been made available by the city of Toronto here :  
- https://www.toronto.ca/ext/open_data/catalog/data_set_files/2016_neighbourhood_profiles.csv  

The Toronto demographic dataset contains multiple features such as :
- Citizenship
- **Ethnic origin**
- Income
- Languages / Mother tongue
- Marital status
- **Neighbourhood information**
- Work activity
- Etc

For this project, we use the **Ethnic origin** and the **Neighbourhood information** for each neighbourhood, in order to cluster the neighbourhoods of Toronto.

**Examples of data from the dataset :**

*Neighbourhood information data :*

| Category                  | Topic                     | Data Source     | Characteristic       | City of Toronto | Agincourt North | Agincourt South-Malvern West | Alderwood      | Annex          | Banbury-Don Mills | Bathurst Manor | Bay Street Corridor | Bayview Village | Bayview Woods-Steeles | Bedford Park-Nortown | Beechborough-Greenbrook | Bendale        | Birchcliffe-Cliffside | Black Creek | Blake-Jones    | Briar Hill-Belgravia | Bridle Path-Sunnybrook-York Mills | Broadview North | Brookhaven-Amesbury | Cabbagetown-South St. James Town | Caledonia-Fairbank | Casa Loma      | Centennial Scarborough | Church-Yonge Corridor | Clairlea-Birchmount | Clanton Park   | Cliffcrest     | Corso Italia-Davenport | Danforth       | Danforth East York | Don Valley Village | Dorset Park            | Dovercourt-Wallace Emerson-Junction | Downsview-Roding-CFB | Dufferin Grove | East End-Danforth | Edenbridge-Humber Valley | Eglinton East | Elms-Old Rexdale | Englemount-Lawrence    | Eringate-Centennial-West Deane | Etobicoke West Mall | Flemingdon Park | Forest Hill North | Forest Hill South | Glenfield-Jane Heights | Greenwood-Coxwell | Guildwood      | Henry Farm     | High Park North | High Park-Swansea | Highland Creek | Hillcrest Village | Humber Heights-Westmount | Humber Summit | Humbermede | Humewood-Cedarvale | Ionview | Islington-City Centre West | Junction Area  | Keelesdale-Eglinton West | Kennedy Park | Kensington-Chinatown | Kingsview Village-The Westway | Kingsway South | Lambton Baby Point | L'Amoreaux             | Lansing-Westgate | Lawrence Park North | Lawrence Park South | Leaside-Bennington | Little Portugal | Long Branch    | Malvern                | Maple Leaf     | Markland Wood  | Milliken       | Mimico (includes Humber Bay Shores) | Morningside | Moss Park      | Mount Dennis | Mount Olive-Silverstone-Jamestown | Mount Pleasant East | Mount Pleasant West | New Toronto    | Newtonbrook East | Newtonbrook West | Niagara        | North Riverdale | North St. James Town | Oakridge | Oakwood Village | O'Connor-Parkview | Old East York  | Palmerston-Little Italy | Parkwoods-Donalda | Pelmo Park-Humberlea | Playter Estates-Danforth | Pleasant View  | Princess-Rosethorn | Regent Park | Rexdale-Kipling | Rockcliffe-Smythe | Roncesvalles   | Rosedale-Moore Park | Rouge          | Runnymede-Bloor West Village | Rustic | Scarborough Village | South Parkdale | South Riverdale | St.Andrew-Windfields | Steeles                | Stonegate-Queensway | Tam O'Shanter-Sullivan | Taylor-Massey | The Beaches    | Thistletown-Beaumond Heights | Thorncliffe Park | Trinity-Bellwoods | University     | Victoria Village | Waterfront Communities-The Island | West Hill | West Humber-Clairville | Westminster-Branson    | Weston | Weston-Pelham Park | Wexford/Maryvale | Willowdale East | Willowdale West | Willowridge-Martingrove-Richview | Woburn | Woodbine Corridor | Woodbine-Lumsden | Wychwood       | Yonge-Eglinton | Yonge-St.Clair | York University Heights | Yorkdale-Glen Park     | 
|---------------------------|---------------------------|-----------------|----------------------|-----------------|-----------------|------------------------------|----------------|----------------|-------------------|----------------|---------------------|-----------------|-----------------------|----------------------|-------------------------|----------------|-----------------------|-------------|----------------|----------------------|-----------------------------------|-----------------|---------------------|----------------------------------|--------------------|----------------|------------------------|-----------------------|---------------------|----------------|----------------|------------------------|----------------|--------------------|--------------------|------------------------|-------------------------------------|----------------------|----------------|-------------------|--------------------------|---------------|------------------|------------------------|--------------------------------|---------------------|-----------------|-------------------|-------------------|------------------------|-------------------|----------------|----------------|-----------------|-------------------|----------------|-------------------|--------------------------|---------------|------------|--------------------|---------|----------------------------|----------------|--------------------------|--------------|----------------------|-------------------------------|----------------|--------------------|------------------------|------------------|---------------------|---------------------|--------------------|-----------------|----------------|------------------------|----------------|----------------|----------------|-------------------------------------|-------------|----------------|--------------|-----------------------------------|---------------------|---------------------|----------------|------------------|------------------|----------------|-----------------|----------------------|----------|-----------------|-------------------|----------------|-------------------------|-------------------|----------------------|--------------------------|----------------|--------------------|-------------|-----------------|-------------------|----------------|---------------------|----------------|------------------------------|--------|---------------------|----------------|-----------------|----------------------|------------------------|---------------------|------------------------|---------------|----------------|------------------------------|------------------|-------------------|----------------|------------------|-----------------------------------|-----------|------------------------|------------------------|--------|--------------------|------------------|-----------------|-----------------|----------------------------------|--------|-------------------|------------------|----------------|----------------|----------------|-------------------------|------------------------| 
| Neighbourhood Information | Neighbourhood Information | City of Toronto | Neighbourhood Number | n/a             | 129             | 128                          | 20             | 95             | 42                | 34             | 76                  | 52              | 49                    | 39                   | 112                     | 127            | 122                   | 24          | 69             | 108                  | 41                                | 57              | 30                  | 71                               | 109                | 96             | 133                    | 75                    | 120                 | 33             | 123            | 92                     | 66             | 59                 | 47                 | 126                    | 93                                  | 26                   | 83             | 62                | 9                        | 138           | 5                | 32                     | 11                             | 13                  | 44              | 102               | 101               | 25                     | 65                | 140            | 53             | 88              | 87                | 134            | 48                | 8                        | 21            | 22         | 106                | 125     | 14                         | 90             | 110                      | 124          | 78                   | 6                             | 15             | 114                | 117                    | 38               | 105                 | 103                 | 56                 | 84              | 19             | 132                    | 29             | 12             | 130            | 17                                  | 135         | 73             | 115          | 2                                 | 99                  | 104                 | 18             | 50               | 36               | 82             | 68              | 74                   | 121      | 107             | 54                | 58             | 80                      | 45                | 23                   | 67                       | 46             | 10                 | 72          | 4               | 111               | 86             | 98                  | 131            | 89                           | 28     | 139                 | 85             | 70              | 40                   | 116                    | 16                  | 118                    | 61            | 63             | 3                            | 55               | 81                | 79             | 43               | 77                                | 136       | 1                      | 35                     | 113    | 91                 | 119              | 51              | 37              | 7                                | 137    | 64                | 60               | 94             | 100            | 97             | 27                      | 31                     |  

We can see : 
- We have the **name of each neighbourhood** in each column name (starting at position 6)
- The **neighbourhood number** (also called CDN number) in the first row (starting at position 6)

*Ethnic origin data* :

| Category                  | Topic                     | Data Source     | Characteristic       | City of Toronto | Agincourt North | Agincourt South-Malvern West | Alderwood      | Annex          | Banbury-Don Mills | Bathurst Manor | Bay Street Corridor | Bayview Village | Bayview Woods-Steeles | Bedford Park-Nortown | Beechborough-Greenbrook | Bendale        | Birchcliffe-Cliffside | Black Creek | Blake-Jones    | Briar Hill-Belgravia | Bridle Path-Sunnybrook-York Mills | Broadview North | Brookhaven-Amesbury | Cabbagetown-South St. James Town | Caledonia-Fairbank | Casa Loma      | Centennial Scarborough | Church-Yonge Corridor | Clairlea-Birchmount | Clanton Park   | Cliffcrest     | Corso Italia-Davenport | Danforth       | Danforth East York | Don Valley Village | Dorset Park            | Dovercourt-Wallace Emerson-Junction | Downsview-Roding-CFB | Dufferin Grove | East End-Danforth | Edenbridge-Humber Valley | Eglinton East | Elms-Old Rexdale | Englemount-Lawrence    | Eringate-Centennial-West Deane | Etobicoke West Mall | Flemingdon Park | Forest Hill North | Forest Hill South | Glenfield-Jane Heights | Greenwood-Coxwell | Guildwood      | Henry Farm     | High Park North | High Park-Swansea | Highland Creek | Hillcrest Village | Humber Heights-Westmount | Humber Summit | Humbermede | Humewood-Cedarvale | Ionview | Islington-City Centre West | Junction Area  | Keelesdale-Eglinton West | Kennedy Park | Kensington-Chinatown | Kingsview Village-The Westway | Kingsway South | Lambton Baby Point | L'Amoreaux             | Lansing-Westgate | Lawrence Park North | Lawrence Park South | Leaside-Bennington | Little Portugal | Long Branch    | Malvern                | Maple Leaf     | Markland Wood  | Milliken       | Mimico (includes Humber Bay Shores) | Morningside | Moss Park      | Mount Dennis | Mount Olive-Silverstone-Jamestown | Mount Pleasant East | Mount Pleasant West | New Toronto    | Newtonbrook East | Newtonbrook West | Niagara        | North Riverdale | North St. James Town | Oakridge | Oakwood Village | O'Connor-Parkview | Old East York  | Palmerston-Little Italy | Parkwoods-Donalda | Pelmo Park-Humberlea | Playter Estates-Danforth | Pleasant View  | Princess-Rosethorn | Regent Park | Rexdale-Kipling | Rockcliffe-Smythe | Roncesvalles   | Rosedale-Moore Park | Rouge          | Runnymede-Bloor West Village | Rustic | Scarborough Village | South Parkdale | South Riverdale | St.Andrew-Windfields | Steeles                | Stonegate-Queensway | Tam O'Shanter-Sullivan | Taylor-Massey | The Beaches    | Thistletown-Beaumond Heights | Thorncliffe Park | Trinity-Bellwoods | University     | Victoria Village | Waterfront Communities-The Island | West Hill | West Humber-Clairville | Westminster-Branson    | Weston | Weston-Pelham Park | Wexford/Maryvale | Willowdale East | Willowdale West | Willowridge-Martingrove-Richview | Woburn | Woodbine Corridor | Woodbine-Lumsden | Wychwood       | Yonge-Eglinton | Yonge-St.Clair | York University Heights | Yorkdale-Glen Park     |
|---------------------------|---------------------------|-----------------|----------------------|-----------------|-----------------|------------------------------|----------------|----------------|-------------------|----------------|---------------------|-----------------|-----------------------|----------------------|-------------------------|----------------|-----------------------|-------------|----------------|----------------------|-----------------------------------|-----------------|---------------------|----------------------------------|--------------------|----------------|------------------------|-----------------------|---------------------|----------------|----------------|------------------------|----------------|--------------------|--------------------|------------------------|-------------------------------------|----------------------|----------------|-------------------|--------------------------|---------------|------------------|------------------------|--------------------------------|---------------------|-----------------|-------------------|-------------------|------------------------|-------------------|----------------|----------------|-----------------|-------------------|----------------|-------------------|--------------------------|---------------|------------|--------------------|---------|----------------------------|----------------|--------------------------|--------------|----------------------|-------------------------------|----------------|--------------------|------------------------|------------------|---------------------|---------------------|--------------------|-----------------|----------------|------------------------|----------------|----------------|----------------|-------------------------------------|-------------|----------------|--------------|-----------------------------------|---------------------|---------------------|----------------|------------------|------------------|----------------|-----------------|----------------------|----------|-----------------|-------------------|----------------|-------------------------|-------------------|----------------------|--------------------------|----------------|--------------------|-------------|-----------------|-------------------|----------------|---------------------|----------------|------------------------------|--------|---------------------|----------------|-----------------|----------------------|------------------------|---------------------|------------------------|---------------|----------------|------------------------------|------------------|-------------------|----------------|------------------|-----------------------------------|-----------|------------------------|------------------------|--------|--------------------|------------------|-----------------|-----------------|----------------------------------|--------|-------------------|------------------|----------------|----------------|----------------|-------------------------|------------------------| 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |   North American Aboriginal origins       | "35,630"  | 40      | 105     | 305     | 475     | 230     | 90      | 250     | 110     | 110 | 100     | 85  | 300     | 625     | 220     | 345     | 135     | 40      | 180     | 135     | 315     | 65  | 180     | 250     | 635     | 445     | 115     | 415     | 240     | 260     | 420     | 105     | 285     | 650     | 395     | 235     | 610     | 185     | 325     | 85      | 110     | 265     | 120     | 100     | 125     | 115     | 155     | 365     | 140     | 130 | 455     | 450     | 75      | 30  | 75  | 20  | 90      | 240     | 200     | 465     | 375     | 140 | 365     | 265     | 145     | 95      | 195     | 195     | 100     | 105     | 195     | 305     | 420     | 280     | 335     | 15  | 85      | 30      | 610     | 205     | 435     | 180     | 185     | 320     | 405     | 330     | 50  | 70      | 500     | 225     | 265     | 290     | 300     | 630     | 190     | 360     | 590     | 105     | 145     | 85      | 80      | 240     | 105     | 400     | 330     | 270     | 285     | 210     | 55  | 330     | 655     | 830     | 105     | 30  | 355     | 225     | 235     | 565     | 65  | 130     | 255     | 135     | 355     | 965     | 755     | 155     | 110     | 230     | 220     | 270     | 205     | 105     | 130     | 605     | 425     | 270     | 335     | 140     | 215     | 220     | 105     | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |     First Nations (North American Indian) | "27,610"  | 25      | 90      | 200     | 345     | 175     | 75      | 205     | 90      | 75  | 95      | 60  | 255     | 430     | 150     | 275     | 115     | 35      | 170     | 110     | 230     | 50  | 135     | 215     | 540     | 320     | 90      | 325     | 200     | 245     | 320     | 100     | 225     | 535     | 365     | 195     | 485     | 155     | 285     | 65      | 100     | 185     | 95      | 75      | 100     | 100     | 110     | 260     | 110     | 120 | 355     | 355     | 65      | 25  | 60  | 10  | 70      | 175     | 150     | 350     | 295     | 105 | 270     | 150     | 105     | 70      | 125     | 155     | 70      | 75      | 115     | 210     | 285     | 220     | 270     | 10  | 55      | 20      | 445     | 180     | 335     | 140     | 145     | 240     | 330     | 260     | 50  | 35      | 340     | 165     | 205     | 260     | 240     | 540     | 165     | 250     | 420     | 65      | 125     | 55      | 60      | 165     | 95      | 355     | 250     | 170     | 185     | 140     | 45  | 225     | 525     | 630     | 95      | 35  | 265     | 165     | 205     | 400     | 65  | 90      | 175     | 90      | 305     | 665     | 680     | 110     | 50      | 210     | 200     | 210     | 165     | 60      | 110     | 470     | 355     | 235     | 275     | 90      | 130     | 200     | 85      | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |     Inuit                                 | 515       | 0       | 0       | 15      | 20      | 10      | 0       | 10      | 0       | 0   | 0       | 10  | 0       | 10      | 0       | 0       | 0       | 0       | 0       | 0       | 10      | 0   | 0       | 0       | 10      | 10      | 0       | 0       | 0       | 0       | 20      | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 20      | 0       | 0       | 0       | 0       | 0   | 10      | 0       | 0       | 0   | 0   | 0   | 10      | 10      | 0       | 10      | 15      | 0   | 10      | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 25      | 0       | 0       | 30      | 0   | 20      | 0       | 10      | 0       | 10      | 0       | 10      | 0       | 0       | 0       | 0   | 0       | 10      | 0       | 10      | 10      | 0       | 0       | 0       | 10      | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 10      | 0       | 10      | 0       | 0   | 0       | 10      | 10      | 10      | 0   | 10      | 0       | 10      | 0       | 0   | 20      | 0       | 10      | 0       | 0       | 10      | 0       | 10      | 0       | 0       | 0       | 10      | 0       | 0       | 25      | 0       | 0       | 10      | 0       | 0       | 0       | 0       | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |     Métis                                 | "8,465"   | 10      | 25      | 100     | 115     | 60      | 0       | 50      | 40      | 30  | 20      | 20  | 70      | 215     | 70      | 65      | 25      | 0       | 15      | 30      | 100     | 25  | 45      | 35      | 130     | 120     | 30      | 100     | 55      | 40      | 100     | 20      | 65      | 170     | 30      | 50      | 135     | 35      | 55      | 25      | 20      | 75      | 30      | 30      | 25      | 10      | 40      | 115     | 20      | 10  | 80      | 90      | 15      | 0   | 20  | 10  | 15      | 70      | 50      | 140     | 100     | 30  | 100     | 110     | 40      | 15      | 75      | 50      | 25      | 25      | 80      | 90      | 165     | 60      | 65      | 10  | 20      | 0       | 145     | 20      | 95      | 35      | 20      | 85      | 95      | 75      | 0   | 30      | 165     | 60      | 55      | 30      | 55      | 85      | 35      | 100     | 165     | 45      | 20      | 25      | 30      | 95      | 10      | 65      | 105     | 110     | 90      | 85      | 10  | 90      | 130     | 215     | 0       | 10  | 80      | 75      | 50      | 180     | 0   | 55      | 75      | 45      | 60      | 305     | 85      | 50      | 30      | 35      | 15      | 50      | 45      | 40      | 35      | 110     | 80      | 60      | 80      | 45      | 75      | 40      | 10      | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |   Other North American origins            | "345,710" | "1,345" | "1,190" | "2,355" | "5,255" | "3,230" | "1,630" | "2,445" | "1,450" | 920 | "4,940" | 620 | "2,915" | "5,365" | "1,840" | "1,700" | "1,180" | "1,615" | "1,570" | "1,555" | "2,080" | 965 | "2,290" | "2,435" | "4,525" | "4,205" | "2,185" | "3,175" | "1,810" | "2,090" | "3,230" | "1,575" | "2,600" | "5,070" | "2,640" | "1,870" | "4,565" | "2,025" | "2,700" | "1,175" | "3,195" | "2,835" | "1,240" | "1,345" | "1,900" | "2,160" | "1,930" | "3,200" | "1,905" | 890 | "3,630" | "4,160" | "1,180" | 925 | 925 | 995 | "1,320" | "2,715" | "1,385" | "4,920" | "2,415" | 800 | "2,120" | "2,235" | "1,820" | "2,090" | "1,355" | "2,880" | "2,030" | "3,650" | "3,825" | "4,045" | "2,590" | "2,270" | "3,785" | 595 | "1,615" | "1,010" | "5,375" | "2,355" | "3,260" | "1,490" | "2,270" | "3,665" | "4,610" | "2,275" | 855 | "1,270" | "5,255" | "2,475" | "1,985" | "1,660" | "2,695" | "3,545" | "1,720" | "2,680" | "4,525" | "1,090" | "1,530" | "1,100" | "1,730" | "1,450" | "1,310" | "2,220" | "2,975" | "4,475" | "4,885" | "2,040" | 745 | "1,925" | "2,935" | "5,445" | "1,800" | 880 | "4,295" | "2,180" | "1,960" | "5,405" | 880 | "1,340" | "2,530" | "1,100" | "1,955" | "9,470" | "4,050" | "2,450" | "1,685" | "1,940" | "1,280" | "3,830" | "2,500" | "1,330" | "2,190" | "5,385" | "3,340" | "1,590" | "2,010" | "2,695" | "2,525" | "2,045" | "1,040" | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |     Acadian                               | "2,315"   | 20      | 0       | 10      | 60      | 0       | 10      | 55      | 10      | 0   | 40      | 0   | 0       | 30      | 10      | 15      | 15      | 0       | 10      | 15      | 15      | 20  | 0       | 0       | 40      | 25      | 0       | 0       | 20      | 10      | 75      | 0       | 0       | 70      | 10      | 10      | 50      | 20      | 10      | 0       | 20      | 10      | 0       | 25      | 10      | 10      | 0       | 15      | 0       | 0   | 30      | 35      | 0       | 0   | 0   | 0   | 0       | 30      | 0       | 25      | 30      | 0   | 0       | 30      | 0       | 0       | 20      | 0       | 15      | 30      | 30      | 65      | 45      | 20      | 30      | 0   | 0       | 0       | 40      | 0       | 30      | 0       | 0       | 30      | 30      | 35      | 0   | 20      | 35      | 30      | 10      | 10      | 30      | 15      | 10      | 25      | 35      | 10      | 30      | 0       | 0       | 10      | 10      | 10      | 30      | 10      | 20      | 30      | 10  | 10      | 25      | 40      | 0       | 0   | 40      | 0       | 20      | 20      | 20  | 10      | 25      | 20      | 15      | 85      | 0       | 20      | 10      | 0       | 0       | 10      | 35      | 0       | 0       | 10      | 45      | 20      | 30      | 10      | 0       | 10      | 0       | 
| Ethnic origin | Ethnic origin population | Census Profile 98-316-X2016001 |     American                              | "27,470"  | 40      | 70      | 100     | 705     | 325     | 105     | 305     | 105     | 105 | 705     | 25  | 180     | 240     | 85      | 200     | 85      | 175     | 130     | 50      | 250     | 75  | 325     | 100     | 425     | 125     | 240     | 140     | 195     | 190     | 280     | 110     | 115     | 560     | 175     | 160     | 335     | 150     | 115     | 80      | 830     | 120     | 65      | 75      | 230     | 260     | 105     | 310     | 140     | 60  | 410     | 600     | 45      | 40  | 30  | 20  | 40      | 320     | 55      | 360     | 255     | 70  | 90      | 180     | 130     | 180     | 95      | 160     | 200     | 370     | 450     | 305     | 275     | 205     | 160     | 25  | 120     | 0       | 425     | 65      | 245     | 90      | 80      | 380     | 365     | 155     | 50  | 100     | 395     | 375     | 160     | 65      | 240     | 140     | 85      | 310     | 300     | 0       | 145     | 60      | 190     | 95      | 40      | 135     | 235     | 690     | 230     | 220     | 40  | 80      | 250     | 430     | 150     | 20  | 315     | 85      | 90      | 450     | 25  | 85      | 260     | 150     | 135     | 720     | 130     | 60      | 110     | 140     | 85      | 135     | 155     | 155     | 145     | 140     | 275     | 95      | 275     | 320     | 280     | 175     | 100     | 

We can see :
- We have the **name of each neighbourhood** in each column name (starting at position 6)
- We have the **name of each ethnic origin** in the Characteristic column
- The **number of people living in each neighbourhood**, associated to each ethnic origin name.

#### 2.2 - List of venues by neighbourhood using the FoursquareAPI

In order to obtain the list of venues, and especially the list of restaurants with the same type as the one we want to open, we are going to request FoursquareAPI with an Explore query.  
The documentation for the Explore query can be found here :
- https://developer.foursquare.com/docs/api/venues/explore  

We query FoursquareAPI suplying the neighbourhood's information (coordinates calculated with the **Geocoder** package), the radius of scan, and the limit of number of venues we want to retrieve.  

Here is an example of a place in a specific neighbourhood retrieved from a FoursquareAPI call :

```json
"response": {
  "headerLocation": "Lawrence Park South",
  "headerFullLocation": "Lawrence Park South, Toronto",
  "headerLocationGranularity": "neighborhood",
  "totalResults": 5,
  "suggestedBounds": {
  "ne": {
  "lat": 43.71824100630001,
  "lng": -79.41042043977797
  },
  "sw": {
  "lat": 43.705640993699994,
  "lng": -79.42781956022205
  }
  },
  "groups": [
    {
      "type": "Recommended Places",
      "name": "recommended",
      "items": [
        {
          "reasons": {
            "count": 0,
            "items": [
              {
                "summary": "Ce site est populaire",
                "type": "general",
                "reasonName": "globalInteractionReason"
              }
            ]
          },
          "venue": {
            "id": "5bbc5b610d173f002c4148f4",
            "name": "Wooden Woodworking Canada Inc.",
            "location": {
              "address": "22 Melham Ct, #1",
              "lat": 43.71708562332913,
              "lng": -79.41977977752686,
              "labeledLatLngs": [
                {
                  "label": "display",
                  "lat": 43.71708562332913,
                  "lng": -79.41977977752686
                }
              ],
              "distance": 575,
              "postalCode": "M1B 2T7",
              "cc": "CA",
              "city": "Scarborough",
              "state": "ON",
              "country": "Canada",
              "formattedAddress": [
                "22 Melham Ct, #1",
                "Scarborough ON M1B 2T7",
                "Canada"
              ]
            },
            "categories": [
              {
                "id": "545419b1498ea6ccd0202f58",
                "name": "Service à domicile",
                "pluralName": "Réparations et services à domicile",
                "shortName": "Services à domicile",
                "icon": {
                "prefix": "https://ss3.4sqi.net/img/categories_v2/shops/hardware_",
                "suffix": ".png"
              },
              "primary": true
              }
            ],
            "photos": {
            "count": 0,
            "groups": []
            }
          },
          "referralId": "e-0-5bbc5b610d173f002c4148f4-0"
        },
      ]
    }
  ]
}
```

We can see : 
- The place comes from the *Lawrence Park South* : **headerLocation tag**
- The name of the place is *Wooden Woodworking Canada Inc.* : **Group -> Items -> Venue -> Name tag**
- The category of the place is *Service à domicile* (english translation : Home service) : **Group -> Items -> Venue -> Categories -> Name tag**


### 3.Methodology 

As we previously saw, we use the following datasets :

- A list of general information about the neighbourhoods (Neighbourhood name, Number, and coordinates calculated using the Geocoder package)
- A list of demographic data about the neighbourhoods, with the number of people of each ethnic origin living in these neighbourhoods

#### 3.1 - Data analysis

A good way to start our analysis is to draw each neighbourhood over the map of the city of Toronto, in order to check if the dataset with the list of neighbourhoods is complete and covers the whole city. For that, we need each neighbourhood' coordinates.  

As we saw, the neighbourhoods' coordinates are not available in the **Neighbourhood information data** dataset. So we are going to retrieve them using the **Geocoder** package. We then store each neighbourhood's coordinates into a dataframe, like this :  

|CDN                        |City_Area                  |Latitude                   |Longitude                  |
|---------------------------|---------------------------|---------------------------|---------------------------|
|129|Agincourt North|43.80930|-79.26707|
|128|Agincourt South-Malvern West|43.78735|-79.26941
|20|Alderwood|43.60496|-79.54116
|95|Annex|43.66936|-79.40280
|42|Banbury-Don Mills|43.74041|-79.34852

The map of the city is displayed using the **Folium package**. On this map, we draw a blue circle for each neighbourhood, using the neighbourhoods' coordinates. It is a good way to visualise the position of each neighbourhood in our dataset. It also confirms that the different neighbourhoods are well distributed within the city, and that our dataset covers the whole city (no missing neighbourhood).  

![Toronto screenshot](images/Toronto1.PNG?raw=true)

Once the map with the neighbourhoods is displayed, we need to find out what are the top most common ethnic origins for each neighbourhood, in order to prepare our data for clustering by demographic data.  
**We do this by counting the number of occurrences of each ethnic origin for each neighbourhood, and sorting the ethnic origins by number of occurence descending.**  

Here are two examples of neighbourhoods, with their top 5 most common ethnic origins of habitants, sorted by count descending :  

**Agincourt North**

|Origin                     |Count                      |
|---------------------------|---------------------------|
|Chinese|16950.0|
|Sri Lankan|2230.0|
|East Indian|2090.0|
|Filipino|1465.0|
|Canadian|1295.0|

**Alderwood**

|Origin                     |Count                      |
|---------------------------|---------------------------|
|English     |2320.0|
|Canadian    |2245.0|
|Irish       |1900.0|
|Scottish    |1720.0|
|Italian     |1275.0|

This will allow us to perform a clustering based on demographic data.  

#### 3.2 - Machine learning algorithm used

For the clustering, we use a **K-Means algorithm**. I chose to use a K-Means algorithm, as it is one on the most used algorithm for unsupervised learning and clustering. It is typically used for scenarios like understanding the population demomgraphics, market segmentation, social media trends, anomaly detection, etc... where the clusters are unknown to begin with. It is exactly our scenario, as we want to understand how the neighbourhoods of Toronto are segmented, and the clusters to begin with are unknown in this situation.  
Also, K-Means is one of the simplest clustering algorithm to implement and to run, and is less time consuming than other, more complex algorithms.  

As we can see, the number of occurences in the demographic data is a numerical value. This means that we can directly use this data for the clustering, we don't need to use any One Hot Encoding.  

In order to determine the best number of clusters for our dataset, which is the optimal K for our K-means algorithm, we are going to use the **Elbow method** as described here :  
https://blog.cambridgespark.com/how-to-determine-the-optimal-number-of-clusters-for-k-means-clustering-14f27070048f  

The Elbow method is a method to find the most appropriate number of clusters in a dataset, by **running several K-means algorithm and comparing the sum of squared distances of samples to the nearest cluster centre**. The more the sum of squared distance is, the further the datapoints are globally from their cluster centre. But we don't have to set K too high, as if K is set to the number of datapoints, then each sample will form its own cluster meaning sum of squared distances equals zero, which is not a good clustering.  

![Elbow method](images/Elbow.PNG?raw=true) 

We are going to use **K = 5**, as the elbow is higly visible for this value.  

Once the clustering is done, we obtain a dataset like this (example with two neighbourhoods from two different clusters) :

|CDN|City_Area|Latitude|Longitude|Cluster Labels|1st Most Common Origin|2nd Most Common Origin|3rd Most Common Origin|4th Most Common Origin|5th Most Common Origin|6th Most Common Origin|7th Most Common Origin|8th Most Common Origin|9th Most Common Origin|10th Most Common Origin|
|---|---------|--------|---------|--------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|-----------------------|
|129|Agincourt North	|43.80930	|-79.26707	|3	|Chinese	|Sri Lankan	|East Indian	|Filipino	|Canadian	|English	|Tamil	|Jamaican	|Scottish	|Irish|
|20	|Alderwood	|43.60496	|-79.54116	|0	|English	|Canadian	|Irish	|Scottish	|Italian	|Polish	|German	|French	|Ukrainian	|Portuguese|

We have the CDN number, the name of the neighbourhood, the coordinates, the cluster label obtained by the K-means algorithm, and the top most common ethnic origins by neighbourhood.  

We can then visualise the clusters on a Folium map. We display each neighbourhood as a circle on the map, each circle will be coloured according to the cluster they have been categorised into.  

![Toronto screenshot with clusters](images//Toronto2.PNG?raw=true)


### 4.Discussion  

#### 4.1 - Clusters

We obtain the following results :  

##### 4.1.1 - Cluster 0 : European & Canadian (Red colour)

The **Cluster 0** regroups areas higly habited by **European and Canadian people**.
We can see English, Italian, Portuguese, French people ...  
Most of them are positioned in almost all the south of Toronto, and in the downtown.  

For example :  

|CDN|	City_Area	|Latitude	|Longitude	|Cluster Labels|	1st Most Common Origin|	2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin|	5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin|
|---|-----------|---------|-----------|-------------|---------------------------|----------------------|------------------------|------------------|---------------------|-------------------------------|------------------------------|--------------------|------------------|-------------------------|
|20|	Alderwood	|43.604960	|-79.541160|	0	|English	|Canadian	|Irish	|Scottish	|Italian	|Polish	|German|	French|	Ukrainian	|Portuguese|
|	57|	Broadview North	|43.689370	|-79.354290	|0	|English	|Irish	|Scottish	|Greek	|Canadian	|French	|German	|Chinese	|Filipino|	Serbian|
|11	|Eringate-Centennial-West Deane|	43.661910	|-79.577380	|0	|Canadian	|English|	Italian	|Irish	|Scottish	|Ukrainian	|Polish	|German	|Chinese	|Portuguese|
|	101|	Forest Hill South|43.694310|	-79.416100	|0	|Polish	|Canadian	|Russian	|English	|Scottish	|Irish	|Jewish	|German	|French	|Chinese|
|106	|Humewood-Cedarvale	|43.689420	|-79.426980	|0	|Canadian	|English	|Polish	|Scottish	|Irish	|Filipino	|Russian	|German	|Italian	|Jewish|

This cluster would interest anyone which wants to open a **european oriented restaurant**, for example an italian or a french restaurant, as it contains the neighbourhoods with the strongest European tendency within their habitants.  

##### 4.1.2 - Cluster 1 : Asian (Purple colour)

The **Cluster 1** regroups areas higly habited **Chinese people, and people from others countries in Asia**.  
We can see that most of them are positioned at the north of Toronto.  

For example :  

|CDN|	City_Area	|Latitude	|Longitude	|Cluster Labels|	1st Most Common Origin|	2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin|	5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin|
|---|-----------|---------|-----------|-------------|---------------------------|----------------------|------------------------|------------------|---------------------|-------------------------------|------------------------------|--------------------|------------------|-------------------------|
| 127 | Bendale              | 43.75963 | -79.25739 | 1 | Chinese  | East   Indian | Filipino      | Canadian | English      | Scottish | Irish    | Sri   Lankan | Greek  | French   |
| 47  | Don   Valley Village | 43.78552 | -79.35017 | 1 | Chinese  | Filipino      | East   Indian | Iranian  | English      | Canadian | Irish    | Scottish     | Korean | Armenian |
| 126 | Dorset   Park        | 43.75533 | -79.27746 | 1 | Filipino | East   Indian | Chinese       | Canadian | Sri   Lankan | English  | Jamaican | Scottish     | Tamil  | Irish    |
| 53  | Henry   Farm         | 43.77230 | -79.34087 | 1 | Chinese  | East   Indian | Filipino      | Iranian  | Canadian     | English  | Scottish | Irish        | Afghan | Korean   |
| 48  | Hillcrest   Village  | 43.80303 | -79.35346 | 1 | Chinese  | East   Indian | Canadian      | Iranian  | Korean       | English  | Russian  | Scottish     | Polish | Irish    |

This cluster would interest anyone which wants to open an **asian restaurant**, for example a chinese restaurant, as it contains the neighbourhoods with the strongest asian tendency within their habitants.  

##### 4.1.3 - Cluster 2 : Indian (Dark green colour)

The **Cluster 2** concentrates areas haghly habited by Indian people.  
We can see that these areas are located at the edges of Toronto.  

For example :  

|CDN|	City_Area	|Latitude	|Longitude	|Cluster Labels|	1st Most Common Origin|	2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin|	5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin|
|---|-----------|---------|-----------|-------------|---------------------------|----------------------|------------------------|------------------|---------------------|-------------------------------|------------------------------|--------------------|------------------|-------------------------|
| 132 | Malvern                           | 43.80977 | -79.22084 | 2 | East Indian | Sri Lankan | Filipino   | Chinese  | Jamaican | Canadian | English  | Tamil      | Guyanese                      | Pakistani |
| 2   | Mount Olive-Silverstone-Jamestown | 43.74721 | -79.58826 | 2 | East Indian | Iraqi      | Jamaican   | Canadian | Somali   | Italian  | Assyrian | Sri Lankan | Other African origins; n.i.e. | Ghanaian  |
| 131 | Rouge                             | 43.80766 | -79.17405 | 2 | East Indian | Sri Lankan | Canadian   | Filipino | Jamaican | English  | Chinese  | Tamil      | Scottish                      | Irish     |
| 1   | West Humber-Clairville            | 43.71451 | -79.59292 | 2 | East Indian | Jamaican   | Canadian   | Filipino | Italian  | Punjabi  | English  | Guyanese   | Chinese                       | Scottish  |
| 137 | Woburn                            | 43.76730 | -79.22823 | 2 | East Indian | Canadian   | Sri Lankan | Chinese  | Filipino | English  | Irish    | Scottish   | Jamaican                      | Tamil     |

This cluster would interest anyone which wants to open an **indian restaurant**.   

##### 4.1.4 - Cluster 3 : Chinese (Light green colour)

The **Cluster 3** also regroups areas higly habited by asian people, the most common ethnic origin is Chinese.  
We can see that most of them are positioned at the north east of Toronto, next to the cluster 1. This cluster is highly similar to the cluster 1.  

For example :  

|CDN|	City_Area	|Latitude	|Longitude	|Cluster Labels|	1st Most Common Origin|	2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin|	5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin|
|---|-----------|---------|-----------|-------------|---------------------------|----------------------|------------------------|------------------|---------------------|-------------------------------|------------------------------|--------------------|------------------|-------------------------|
| 129 | Agincourt North              | 43.80930 | -79.26707 | 3 | Chinese | Sri Lankan  | East Indian | Filipino    | Canadian | English  | Tamil    | Jamaican | Scottish   | Irish    |
| 128 | Agincourt South-Malvern West | 43.78735 | -79.26941 | 3 | Chinese | East Indian | Filipino    | Sri Lankan  | Canadian | English  | Scottish | Jamaican | Italian    | Irish    |
| 117 | L'Amoreaux                   | 43.79726 | -79.31220 | 3 | Chinese | East Indian | Canadian    | Sri Lankan  | Filipino | English  | Armenian | Jamaican | Scottish   | Irish    |
| 130 | Milliken                     | 43.82280 | -79.27694 | 3 | Chinese | Sri Lankan  | East Indian | Filipino    | Canadian | Tamil    | Jamaican | English  | Vietnamese | Spanish  |
| 51  | Willowdale East              | 43.77248 | -79.40039 | 3 | Chinese | Iranian     | Korean      | East Indian | English  | Canadian | Scottish | Irish    | Russian    | Italian  |

This cluster would interest anyone which wants to open a **chinese restaurant**, or an asian restaurant in general.   

##### 4.1.5 - Cluster 4 : Irish, Scottish & English (Yellow colour)

The **Cluster 4** regroups areas higly habited by **English, Irish, Scottish and Canadian people**.  
We can also see that there are a lot of people from other european countries as well, such as French, German, Polish, ...   
Most of these neighbourhoods are positioned at the south and in the downtown of Toronto.  

For example :  

|CDN|	City_Area	|Latitude	|Longitude	|Cluster Labels|	1st Most Common Origin|	2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin|	5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin|
|---|-----------|---------|-----------|-------------|---------------------------|----------------------|------------------------|------------------|---------------------|-------------------------------|------------------------------|--------------------|------------------|-------------------------|
| 95  | Annex                               | 43.66936 | -79.40280 | 4 | English    | Irish   | Scottish | Canadian | German   | French  | Polish  | Chinese     | Italian  | Russian                       |
| 122 | Birchcliffe-Cliffside               | 43.69472 | -79.26460 | 4 | English    | Irish   | Canadian | Scottish | French   | German  | Chinese | Italian     | Filipino | British Isles origins; n.i.e. |
| 75  | Church-Yonge Corridor               | 43.66024 | -79.37868 | 4 | English    | Irish   | Scottish | Chinese  | Canadian | French  | German  | East Indian | Italian  | Polish                        |                 |
|93	|Dovercourt-Wallace Emerson-Junction	|43.66604	|-79.43687	|4	|Portuguese	|English	|Canadian	|Irish	|Scottish	|Chinese	|Italian	|German	|French	|East Indian|
| 62  | East End-Danforth                   | 43.68415 | -79.29911 | 4 | English    | Irish   | Scottish | Canadian | French   | German  | Chinese | Italian     | Polish   | British Isles origins; n.i.e. |                     |  

The cluster would interest anyone which wants to open an **english or irish pub**, or any UK/Ireland related type of restaurant.  

#### 4.2 - Analyse each neighbourhood's competition

Let's say we want to open an irish pub. We are going to use the **cluster 4** in order to find the best neighbourhood for this will.  
In order to analyse the competition for each neighbourhood, we are going to retrieve the list of existing venues of the type **pub**, in the neighbourhoods categorised as **cluster 4**. For this task, we use **FoursquareAPI**.  

We build a dataframe as such (top 5 rows which represent 5 venues with the Pub category) :  

| CDN | Area Latitude | Area Longitude | Venue                    | Venue Latitude | Venue Longitude | Venue Category |
|-----|---------------|----------------|--------------------------|----------------|-----------------|----------------|
| 95  | 43.66936      | -79.40280      | The   Madison Avenue Pub | 43.667947      | -79.403486      | Pub            |
| 95  | 43.66936      | -79.40280      | Duke   of York           | 43.669186      | -79.397527      | Pub            |
| 75  | 43.66024      | -79.37868      | Churchmouse   & Firkin   | 43.664632      | -79.380406      | Pub            |
| 62  | 43.68415      | -79.29911      | Grover   Pub and Grub    | 43.679181      | -79.297215      | Pub            |
| 62  | 43.68415      | -79.29911      | Mullins   Irish Pub      | 43.680348      | -79.289370      | Pub            |

We can then count the number of existing Pubs for each neighbourhood, and sort these neighbourhoods by count ascending :  

|Count|CDN	|City_Area	|Latitude	|Longitude	|Cluster Labels	|1st Most Common Origin	|2nd Most Common Origin	|3rd Most Common Origin	|4th Most Common Origin	|5th Most Common Origin	|6th Most Common Origin	|7th Most Common Origin	|8th Most Common Origin	|9th Most Common Origin	|10th Most Common Origin	|
|---|-------|------|-----|-----|-----|----|------|-------|------|--------|---------|-------|--------|-------|--------|
|  4  | 16  | Stonegate-Queensway                 | 43.63718 | -79.50058 | 4 |English  | Canadian | Irish    | Scottish | Polish   | Italian  | Ukrainian   | German  | French                        | Portuguese                    |
|15 | 122 | Birchcliffe-Cliffside               | 43.69472 | -79.26460 | 4 | English  | Irish    | Canadian | Scottish | French   | German   | Chinese     | Italian | Filipino                      | British Isles origins; n.i.e. | 
|21| 45  | Parkwoods-Donalda                   | 43.75613 | -79.32880 | 4  | Canadian | English  | Chinese  | Scottish | Irish    | Filipino | East Indian | German  | Jamaican                      | French                        | 
|29 | 70  | South Riverdale                     | 43.65221 | -79.33820 | 4 | Chinese  | English  | Irish    | Scottish | Canadian | French   | German      | Italian | British Isles origins; n.i.e. | Polish                        | 
|30 | 17  | Mimico (includes Humber Bay Shores) | 43.61729 | -79.49885 | 4 | English  | Canadian | Irish    | Scottish | Italian  | Polish   | Ukrainian   | German  | French                        | Chinese                       | 

We assume that the **top 5 neighbourhoods** from this list represent the best places to open a new pub, as :  
- the demographic data shows that people will likely come in this kind of venue in these neighbourhoods
- the competition is limited in these neighbourhoods  

We can draw these 5 neighbourhoods on the map of Toronto :  

![Best places of a pub](images/Toronto3.PNG?raw=true)


### 5.Conclusion  

In this project, we managed to cluster the city of Toronto using **demographic data by neighbourhoods**. This helps us identify which neighbourhoods are the most adequate for opening a new restaurant of a specific type.  

Then, we managed to **identify the neighbourhoods with the less competition** within these adequate neighbourhoods, in order to optimise the performance of this new business.  

**Food service contractors** can use similar data analysis in order **to find the best spots to open a new restaurant**.  
