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

##
