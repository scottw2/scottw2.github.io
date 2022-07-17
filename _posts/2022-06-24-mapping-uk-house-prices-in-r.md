---
layout: post
title: Mapping English and Welsh House Prices in R
description: Mapping English and Welsh House Prices in R
summary: Mapping English and Welsh House Prices in R
comments: true
tags: [R, Leaflet]
---


### Introduction

House prices are constantly in the news, however, basically all the news stories I've read about this topic don't focus on very granular data - instead talking about the country overall, or dividing prices by region and perhaps doing a deep dive into a specific locality. The focus of the post is to therefore look at house prices nationally - at a very local level. This should 1) hopefully show some interesting trends and 2) allow me to learn a bit about making interactive maps in R.


### Data

The data on house prices was taken from the May release of the "Prices Paid" dataset, collected by HM Land Registry. This is a dataset of all registered property sales in England & Wales from 1995 to present. It contains information on the price paid for each property as well as the postcode, address and other info (e.g. property type, new build/old build). Ideally, I wanted to get data for the whole of the UK, but Scotland does not provide this data in an easily accessible manner (as far as I know) and any property data for Northern Ireland apparently requires a paid license to access, so I was left with just English and Welsh data.

To map this data, I needed to match the postcodes to geographic coordinates and geographic areas. I used the ONS National Postcode Lookup to do this. The Postcode Lookup details every postcode in the UK and their associated latitude/longitude as well as the geographic areas that they belong to (e.g. Local Authority District, Middle Super Output Area).

Some other important datasets I needed for creating some of the maps were the shapefiles for the geographic areas I wanted to look at, which were also from the ONS.

One final dataset is from the House of Commons (HoC) Library. For Middle Super Output Areas (MSOA) - which is an area type I wanted to visualise, they generally don't have names and are just named based on their local authority district (e.g. Great Yarmouth 1, Great Yarmouth 2), however the HoC Library has devised actual descriptive names for these areas (e.g. Hemsby & Oremsby, Fleggburgh/ Rollesby & Martham), which are a bit nicer for presenting and analysing the data at a MSOA level.

### General Method

Due to reporting time lags, it's generally not best practice to look at data from the last few months, so I only looked at data up to March 2022. This should hopefully reduce the impact of reporting lags, while also providing fairly up to date figures. 

Additionally, because I am drilling down into rather small areas, just using sales from March 2022 would lead to a very small sample size for a lot of areas, which wouldn't be very accurate. So I decided to look at the median price over the whole year for each area (March 2021 - March 2022). I didn't adjust for property type mix as a lot of house price indexes do, instead opting to look at the unadjusted values.

I also decided to bin the price/sale values for colouring the maps, as I think it makes it easier to visually interpret the difference in price between areas. The bins I used were generally not equal width, but instead were somewhat similar to log scales, where larger values had larger bins, to reduce the total number of bins, while not crowding out the lower prices areas like a continuous scale would. The colour scales used were from the scico and viridis packages, which are perceptually uniform and colourblind friendly, making them good for this sort of visualisation.

To make the maps interactive, I used the Leaflet package in R, which is build on top of the Leaflet JavaScript library. There are quite a lot of interesting features in this package that I tried to make the most of, e.g. adding dynamic lables, using multiple basemaps to show location labels on top of the polygon layers and having multiple polygon layers that are visible at different zoom levels.

#### Chloropleth maps

The first map type I looked at was a chloropleth, shown below. The map initially shows median house prices and the number of sales at a Local Authority District (LAD) level of granularity. However if you zoom in, it will break the LADs down to MSOAs (essentially one layer below - ignoring wards as they don't match perfectly). This allows you to get a broader and less crowded view at the national level and still explore regional variations at a high level of granularity.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/chloropleth2.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>

{::options parse_block_html="true" /} 

<details><summary markdown="span"> Click here for the code that was used to generate this map </summary>

```r
    chloropleth <-  leaflet() %>%  
        setView(lng = -0.5, lat = 53.25, zoom = 6.00) %>% 
        addMapPane("background", zIndex = 100) %>% 
        addMapPane("data", zIndex = 101) %>% 
        addMapPane("labels", zIndex = 102) %>% 
        addProviderTiles(providers$CartoDB.PositronNoLabels, 
                            options = providerTileOptions(pane = "background", minZoom = 6)) %>% 
        addPolygons(data = msoa_leaflet_change,fillColor = ~pal(msoa_leaflet_change$price_bins_post), stroke = TRUE, color = "white",weight = 0.75, fillOpacity = 0.75,
                    label = labels, group = "x", options = pathOptions(pane = "data")) %>% 
        addPolygons(data = lad_leaflet_change, fillColor = ~pal(lad_leaflet_change$price_bins_post), stroke = TRUE, color = "white",weight = 0.75, fillOpacity = 0.75,
                    group = "y", label = labels_x, options = pathOptions(pane = "data")) %>% 
        addProviderTiles(providers$CartoDB.PositronOnlyLabels, 
                            options = providerTileOptions(pane = "labels",minZoom = 6)) %>% 
        groupOptions("x", zoomLevels = 11:20) %>% 
        groupOptions("y", zoomLevels = 0:10) %>% 
        addLegend("bottomright", pal = pal, values = c("0-150k", "150k-250k", "250k-350k", "350k-450k", "450k-750k", "750k-1m", "Above 1m"))
    saveWidget(chloropleth, "Widgets/chloropleth.html")
```

</details>
<br/>

{::options parse_block_html="false" /} 

#### Grid maps

There is also an ``` st_make_grid() ``` function in the sf package that can be used to divide an area into equal sized grid squares and then summarise the data within each grid square. 

The grid squares I used are supposedly 25km^2 for the England and Wales maps and 0.75km^2 for the London map (see both below). Leaflet uses the Web Mercator (3875) coordinate referencing system (CRS) to display maps, which essentially flattens maps to make them look nice for the web. However, it does this at the expense of accurate distances, which gets worse the further you move from the equator. This makes me question how accurate these grid square sizes are. It would probably be better to use a CRS like the UK National Grid (27700), which does not distort distances like the Web Mercator CRS, but leaflet doesn't support this, atleast not if you want to use pretty basemaps.

In any case, these grid squares can be used to create quite detailed maps of house prices and house sales. The main differences compared to chloropleth maps are that grid maps don't say anything about population density/property density and because of this there are quite a lot of grid-squares with just a few observations, which may impact the reliability of the presented median prices. At the same time, using equally sized grid-squares does allow for a more granular view of the actual house prices and sales across the country, which can reveal insight which may have been hidden by using other map types. e.g. you can see a few grid squares with very highly priced properties but only 1 or 2 sales above Erith in the London map below.

Below you can see maps of the UK, coloured firstly by property price and secondly by number of sales.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/price_grid2.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>


<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/sales_grid4.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>


I also created a grid map just for London, as London has a high population (~8.9 million) and a whole bunch of regional inequalities. I therefore thought it would be interesting to visualise it individually. I also used different price bins to better represent London's property market, which is why the colours are different to the other price maps. 

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/london_grid2.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>


#### Point-grid maps

Additionally, the ```st_centroid()``` function can be used to find the centre of each grid-square. From this we can create what I've called "point-grid" maps (not sure if there is an actual name for this kind of map, but I have seen some other examples). These maps can use both colour and size scales to show both total sales and median price, which isn't shown in the other maps here. The drawback of this type of map is that it can become harder to see the individual points in high turnover area e.g. London or Birmingham, due to overlapping points - although a log size scale can somewhat fix this.

See a point-grid map for the UK below, using a logged size scale.

 <div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/log_point_grid2.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>

#### Static maps

Finally, I also put together a static map at the MSOA level for my own amusement:

![](/assets/images/house-prices/Total Plot v6-01.png)