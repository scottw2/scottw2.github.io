---
layout: post-2
title: Industries of Employment
description: Industries of Employment
summary: An analysis of employment in England & Wales.
comments: true
tags: [R, Illustrator]
published: true
image: /assets/images/industries-of-employment/post_image3.png
---

Since June 2022, the Office for National Statistics (ONS) has been slowly releasing the results of the 2021 England & Wales Census, providing a broad overview of life across both UK nations. From what has been released so far, there are various insightful datasets, including one which shows the industries people were employed in when the Census took place.

![](/assets/images/industries-of-employment/Industry-treemap-image.png){:class="img"}


### Data Sources & Methodology

The Census dataset can be found [here](https://www.ons.gov.uk/census/maps/choropleth/work). Within it, employment is categorised by industry using Standard Industrial Classification (SIC) codes. These codes have a number of hierarchical levels, and the Census data appears to use the second highest level. I have therefore incorporated the highest hierarchical level using [this](https://www.ons.gov.uk/methodology/classificationsandstandards/ukstandardindustrialclassificationofeconomicactivities/uksic2007) additional ONS data. From here on, these industry hierarchical levels will be referred to as *higher* and *lower* levels.

The Census data specifically contains the number of people aged 16 and above in each local authority who were in employment when the census took place (15th - 21st March 2021), with the industry they were working in identified based on the information provided about their employer's main activity (SIC code).

From this, it's possible to work out the percentage of people employed in each industry across England & Wales and within each local authority. Note that this doesn't factor in the percentage of people not working.

### National Employment

Figure 1 (below) shows how employment is distributed across England and Wales. The chart displays the percentage of people employed in each lower level Census industry grouped by the higher level industries. Some lower level industries and/or percentages are not labelled due to layout and design constraints.

Looking firstly at the higher level industries, **Wholesale & Retail Trade** is the largest, employing 15% of people, **Human Health & Social Work** is the second largest at 14.7%, and **Education** is in third place with 9.8%.

Conversely, **Activities of Extraterritorial Organisations & Bodies** (i.e embassies or international organisations like the UN) is the smallest industry at 0.04%, **Activities of Households as Employers** (e.g. individuals working for households as gardeners, babysitters & caretakers) is the second smallest with 0.05%, followed by **Mining & Quarrying** at 0.15%.

Zooming into the lower level industries, The largest lower level industries are **Retail trade (excluding motor vehicles & motorcycles)** at 10.2% of employment, followed by **Education** with 9.8% and then **Human health activities** with 8.9%. It's worth noting that some of the lower level industries don't actually break down the higher level industry classification - Education is a good example of this as this sector has the same figure for both levels of the hierarchy (9.8%).

The smallest lower level industry is **Undifferentiated goods- and services-producing activities of private households for own use** (whatever that means) which employs 8 people in the whole of England and Wales. The second smallest is **Mining of metal ores** at 0.002% (529 people employed), and the third smallest is **Mining of coal & lignite** at 0.007% (1960 workers).

Some other interesting observations are that **Legal & accounting services** only makes up 2.2% of employment, which is quite a lot lower than I expected, given the prominence of the big accounting firms. In a similar way, **Financial services** (1.8%) is smaller than I thought it would be.  Employment in the supply of utilities also appears quite low compared to my expectations, with only 0.6% working the **Electricity, Gas, Steam & Air Conditioning Supply** sector and 0.7% employed in the **Water Supply, Sewerage & Waste Management** Industry. The **Construction** industry is however slightly larger than I anticipated, employing 8.7% of workers, but I suppose this is expected given the wide variety of roles involved. Additionally, perhaps some of the construction-orientated roles within the utilities sector are classified as being in the construction industry, due to the large amount of outsourcing in this sector.

![](/assets/images/industries-of-employment/Industry-treemap.png){:class="img-pretty-large"}
*Figure 1: Employment by Industry*


### Distribution of Employment

At the sub-national level, there's quite a wide variation in the percentage of people employed in each specific industry. This distribution is shown for higher level industries in Figure 2. 

Some higher level industries, like **Real Estate**, have a relatively small range of variation, whereas others such as **Agriculture, Forestry & Fishing** and **Finance & Insurance** have rather wide distributions. This is partly due to differences in absolute employment figures between industries, but also shows which industries have very high concentrations in some areas but few workers in others - this is expanded on in the next section, which looks at employment figures relative to the national average.

Figure 2 also highlights various intriguing outliers. For example, Powys in Wales has the highest percentage of employment in **Agriculture, Forestry & Fishing** (9.4%). This appears to be driven by a large amount of agricultural work in Powys, which has the lowest population density in England & Wales (26 residents per sq. km).

At the other end of the scale, the City of London unsurprisingly has 0% of it's workers employed in **Agriculture**, but instead 20.0% are employed in **Finance & Insurance** and 23.6% in **Professional, Technical & Scientific Services** (which includes sectors like legal & accounting services as well as management consulting), reflecting the City's position as one of the financial and professional services capitals of the World.

Richmondshire also stands out for having by far the highest percentage of employment in **Public Administration & Defence**, at 20.8%. This is probably due Catterick Garrison being located there -  a military town with a population of about 13,000 people.

![](/assets/images/industries-of-employment/Industry-beeswarm.png){:class="img-pretty-large"}
*Figure 2: Distribution of Employment across Local Authorities*

### Geographic Differences

Furthermore, geographic differences in employment are displayed in Figure 3, which shows the percentage deviation from the national average of the percentage employed in each higher level industry (a bit of a mouthful, I know). Note that the 5 smallest industries (making up less than 2% of employment in total) have not been included in this visual as it was a bit too crowded.

Some industries have less overall percentage variation from the average than others e.g. **Wholesale & Retail Trade** and **Human Health & Social Work**. This appears to be the case for industries that are larger and fairly essential to have across the whole country - Human Health & Social Work being a prime example.

However, other industries, like **Agriculture, Forestry & Fishing** or **Information & Communication** have a large overall variation from the average, driven by the variable pros and cons of industries locating in each local authority. For example, white-collar industries tend to be more urban-centric, with a particular focus on London & the South East e.g. **Finance & Insurance**, **Professional, Scientific & Technical Services** and **Information & Communication**. 

**Manufacturing** has a fairly opposite profile, being located mostly outside of the South East and especially around the Midlands, mainly due to historic ties to this part of the UK. Similarly, **Agriculture, Forestry & Fishing** unsurprisingly is very rurally focused, which shouldn't need any further explanation. 

**Accommodation & Food Services** also appears to be relatively more prevalent in touristy areas e.g. the Lake District, Cornwall & North Norfolk as well as central London.

The **Education** industry tends to have a relatively high prevalence in University towns, e.g. Oxford, Cambridge, York, Exeter, but has a low relative variation elsewhere.

**Transportation and Storage** is more prevalent around transportation hubs like Heathrow, Felixstowe & Tilbury, but interestingly, this industry is also relatively more prevalent up and down the centre of England, which makes sense considering the logistical advantages of locating warehouses and transportation services in this area (e.g. good motorway access and a very central location allowing for quick transportation to most areas of the UK).

![](/assets/images/industries-of-employment/industry-map-perc.png){:class="img-pretty-large"}
*Figure 3: Geographic Distribution of Employment*

