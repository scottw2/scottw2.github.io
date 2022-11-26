---
layout: post-2
title: Political Donations
description: Political Donations
summary: Showing the flow of donations to UK political parties since 2001.
comments: true
tags: [R, Illustrator]
published: true
image: /assets/images/political-donations/post_image.png
---




### Data

The data was sourced from the Electoral Commission's (EC's) database of donations to British political parties. 

The dataset runs from 2001 and includes every donation over £xxxx, as well as some additional donations under this quantity.

For each donation, the value, donor's name and donor type is recorded (e.g. individual, company, trade union), as well as the dates the donation was offered, accepted and then reported to the EC. The party receiving the donation is of course also included.

### Donations Flows

![](/assets/images/political-donations/bumpchart28Lfont.png)


### Where Donations Come From

![](/assets/images/political-donations/alluvialchart6.png)

### Largest Donations

I initially wanted to visualise the largest donors to each party, however the data quality of donor names was absolutely terrible. For example,  one of the largest donors, Christopher Harborne, has donations under six different names in the dataset. Unfortunately there didn't appear to be a particularly quick way of cleaning this data so I opted to just look at the largest donations that have been made to each party.

![](/assets/images/political-donations/circlepacking9.png)

