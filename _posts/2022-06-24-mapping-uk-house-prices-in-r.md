---
layout: post
title: Mapping English and Welsh House Prices in R
description: Mapping English and Welsh House Prices in R
summary: Mapping English and Welsh House Prices in R
comments: true
tags: [R, Leaflet]
---


## Introduction

Rising house prices have been all over the news for the past about 5 years in the UK. Since the pandemic struck, the rate of increase has shot up across most of the country. However, basically any news story I've read about house prices doesn't really focus on very granular data - usually talking about the country overall, or dividing by region and perhaps doing a deep dive into a specific locality. The focus of the post is to look at house prices at a very local level, which 1) should hopefully show some interesting trends and 2) allows me to learn a bit about making interactive maps in R.


## Data

Data on house prices was taken from the April release of the "Prices Paid" dataset, Collected by HM Land Registry. This is a dataset of all registered property sales in UK from 1995 to present. It contains information on the price paid for each property as well as the postcode, address and other info (e.g. property type, new build/old build). Ideally, I wanted to get data for the whole of the UK, but Scotland do not provide this data in an easily accessible manner (as far as I know) and any property data for Northern Ireland apparently requires a paid license to access, so I was left with just English and Welsh data.

To map this data, I needed to match the postcodes to geographic coordinates and geographic areas. I used the ONS' National Postcode Lookup to do this. The Postcode Lookup details every postcode in the UK and their associated latitude/longitude as well as the geographic areas that they belong to (e.g. Local Authority District, Middle Super Output Area).

The other main datasets I needed for creating some of the maps were the shapefiles for the geographic areas I wanted to look at, which were also from the ONS.

One final dataset is from the House of Commons Library. For middle super output areas, they generally don't have names and are just named based on their local authority district (e.g.Great Yarmouth 1, Great Yarmouth 2), however the HoC Library has devised actual descriptive names for these areas (e.g. Hemsby & Oremsby, Fleggburgh/ Rollesby & Martham), which area a bit nicer for presenting and analysing the data at a msoa level.

## Data Wrangling


## Maps

### Chloropleth maps

The below map initially shows median house prices and the number of sales at a Local Authority District Level of granularity. However if you zoom it, it will break the LADs down to MSOAs (essentially one layer below - ignoring wards as they don't match perfectly). This allows you to get a broader and less crowded view at the national level and still explore regional variations at a high level of granularity.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/chloropleth.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>

### Grid maps

There are also a couple of functions in the sf package that can be used to divide an area into equal sized grid squares and then summarise the data within each grid square. 

insert code and description of how this was done

This can be used to create quite detailed and cool maps of house prices and house sales. The main differences compared to chloropleth maps are that grid maps don't say anything about population density/property density and because of this there are quite a lot of grid-squares with just a few observations, which may impact the reliability of median prices and could be misleading. At the same time, using equally sized grid-squares does allow for a more granular view of the actual house prices and sales across the country, which can reveal insight which may be hidden by using other map types. e.g. you can see a few grid squares with very highly priced properties but only 1 or 2 sales above Erith in the London map below.

Initially, I couldn't get the grid-squares to be actually square instead of rectangular. But I realised it was basically to do with the coordinate references system and how leaflet interacts with this, so by actually specifying grid squares that were 2/3rd wider than they were tall, the grid-squares appeared square on the output maps.

Below you can see maps of the UK, coloured firstly by property price and secondly by number of sales.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/sales_grid.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>


I also created a grid map just for London, as London has a lot of property sales and I therefore thought it would be interesting to visualise it individually. I also added a few more colours to the colour scale and legend to capture the very pricy area of the Capital.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/london_grid.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>


### Point-grid maps

Additionally, the st_centroid function can be used to find the centre of each grid-square. From this we can create what I've called "point-grid" maps (not sure if there is an actual name for this kind of map, but I have seen some other examples). These maps can use both colour and size scales to show both total sales and median price, which isn't shown in the other maps here. The drawdown of this type of map is that it can become harder to see the individual points in high turnover area e.g. London or Birmingham, due to overlapping points.

<div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/point_grid.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe></div> 


 <div style="width:100%;border:none"><iframe
     src="/assets/widgets/house-prices/log_point_grid.html"
     width="100%" height = 500px frameBorder="0"
 ></iframe>   
 </div>

