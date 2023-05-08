---
layout: post-2
title: Mortality & Longevity
description: Mortality & Longevity
summary: Investigating mortality & longevity in England & Wales from 1841 to 2020
comments: false
tags: [R, Illustrator]
published: false
image: /assets/images/mortality/post_image.png
---

MAYBE CHANGE SOME OF THE TENSES HERE TO PAST TENSE - AS IT FEELS WEIRD

USE PAST TENSE WHEN TALKING ABOUT HISTORICAL STUFF

LEGENDS ON MOST GRAPHS ARE NOT CORRECT YET.

DEATHS GRAPH IS NOT ACTUAL DEATHS BUT Dx

A couple of years ago, in one of my previous jobs, I came across the [Human Mortality Database (HMD)](https://www.mortality.org/), which holds a large amount of data on mortality and life expectancy across various countries. Some of this data even goes back hundreds of years (e.g. there is data going back to 1841 for England & Wales and also Swedish data from 1751 - I think this is the earliest record in the database).

Visualising this data can draw out various interesting relationships and trends, many of which can be seen in heatmaps on the [Human Mortality Explorer website](https://jschoeley.shinyapps.io/hmdexp) ([Scholey, 2016](https://paa.confex.com/paa/2016/mediafile/ExtendedAbstract/Paper6383/3138944_schoeley-2016-hmd_explorer.pdf)). These charts were really the inspiration and starting point of this project. This project builds on these visualisations, with a focus just on England & Wales, and aims to visualise and analyse mortality and longevity over time, looking at overall figures, and breaking the data down by age and gender.

Additionally, The project expands on the analysis available from the HMD data, by looking into the cause of death in England and Wales across ages between 1900 & 2020, using a somewhat similar methodology to [Maiolo & Reid, 2020](https://www.sciencedirect.com/science/article/pii/S2352827319303040). This shows how deaths from various causes have waxed and waned over the years, while also providing insight into how disease classifications and medical knowledge have changed over time.

### Data

As mentioned above, most of the data came from the HMD. This data covers England & Wales and includes total population - i.e. it includes military deaths, notably from WW1 & WW2. Morality rates and life expectancy figures were sourced from annual period life table data broken up by age at yearly intervals (apart from ages >= 110, which were bundled together) from 1841 to 2020. Historic data on actual deaths per age group was sourced from a seperate file from the HMD.

There are a few main caveats to the HMD data. ........... For other caveats and a detailed description of how the datasets were put together [see here](https://www.mortality.org/File/GetDocument/hmd.v6/GBRTENW/Public/InputDB/GBRTENWcom.pdf) and [here](https://www.mortality.org/File/GetDocument/Public/Docs/MethodsProtocolV6.pdf)

The data for cause of death was sourced from the ONS' 20th Century Mortality files and the (whereever 21st C data is from). This data shows the total deaths from each cause by year, grouped into age bins (e.g. 0-1,1-10) across time. 

There were 2 main issues with this dataset. Firstly, the International Classification of Diseases (ICD) was used to categorise cause of death. However, the ICD has changed significantly over time, going through more than 10 iterations (usually there was a new version every 10 or so years). This is partly because our understanding of diseases has improved greatly as medical science has progressed over the years. At the same time, certain diseases have become more or less prominent over time. Combining both of these factors results in the ICD needing to be regularly updated. However, this of course makes it difficult to compare causes of death over time. Maiolo & Reid, 2020 attempted to harmonise the different versions of the ICD by assigning diseases to one of x groups (e.g. Infections, Respiratory issues), and I didn't (and still don't) know particularly much about disease classification I used the same approach.

The second issue was that deaths were grouped into age bins, but I ideally wanted to visualise the data for each year of age to maintain consistency with the rest of the visualisations here. One way to accomplish this was to estimate the distributions from the binned data. I did this using the R ungroup package ([Pascariu et al., 2018](https://joss.theoj.org/papers/10.21105/joss.00937)).

Insert methodology for getting deaths by cause. (once finalised) - keep tenses consistent (mostly past tense)

### Changes Over Time



![](/assets/images/mortality/Industry-beeswarm20.png){:class="img-somewhat-large"}
*Figure 1: Life expectancy at birth over time*





![](/assets/images/mortality/life_exp1.png){:class="img"}
*Figure 1: Life expectancy at birth over time*

**insert graph on Life expectancy over time - talk about what life expectancy at birth actuall means and what it doesn't**

**insert a small paragraph to link morality and life expectancy**

Figure 2 shows how mortality rates have changed over time across ages. In the 19th century, mortality rates for infants and young children were particularly high, due to xxxxxxxxxx (lack of antibiotics? etc). At the same time, people died much earlier than today ............. 

The two World Wars are also very visible, with large increases in morality rates for those between the age of 18-50, with the vast majority of these deaths being conscripted men. It's interesting that further into the wars, higher mortality rates tended to affect a larger number of ages, possibly due to upper conscription age limits being widened and other restrictions on conscription being scrapped (e.g. married men were initially exempt during WW1). The 1918 Spanish Flu pandemic is also visible at the tail end of WW2, this led to an xx rise in mortality rates for yy ages.

Furthermore, The impact of medical advances (particularly the discovery of penicillin) during World War 2 is quite apparent, shown by the far lower and continually decreasing mortality rates for children and young adults after the end of the war. The lower number of deaths from infections also reveals that morality rates increase at around age 18, caused by a larger amount of accidents and suicides amongst young adults compared to children (driven mostly by male deaths).

![](/assets/images/mortality/mortality11.png){:class="img"}
*Figure 2: Mortality rates by age and year*

Across the whole 1841-2020 window it's also possible to see a general pattern of people dying at older ages as time has gone by, shown by the changing colours at each age. Figure 3 presents this in more detail, showing the percentage of annual deaths split by age group across this period. 

For example, in 1841, almost 20% of deaths were infant deaths, but only yy% were above the age of 80. Compare this to 2020, where only x% of deaths were infants - in fact, deaths up to the age of 60 in 2020 took up a lower proportion of overall deaths than infant deaths in 1841 (CHECK THIS). Moreover, in 2020, jj% of deaths were above 80 years old, with about 20% above the age of 90.

![](/assets/images/mortality/deaths6.png){:class="img"}
*Figure 3: Deaths by age group and year*

### Gender Differences

There are various metrics for displaying gender differences in mortality and life expectancy, but ....

The gap in life expectancy at birth between males and females increased from 2.0 years in 1841 to 4.0 years in 2020. However, between these two dates there have been various other interesting developments, as shown in Figure 5. Pre-WW1, the gap increased somewhat linearly by 2.1 years between 1841 & 1913, before shooting up during the Great War, where male life expectancy fell to 20.0 years less than female life expectancy in 1917. There was a similar change during WW2, but less pronounced (maximum gap of 12.9 years). After WW2, there was a visible increase in the life expectancy gap up until a peak of 6.34 years in 1969, after which the the gap started trending downward. There was also a minor, but sharp increase in the life expectancy gap in 2020, likely due to the Covid-19 pandemic.

![](/assets/images/mortality/gender_diff_life_exp1.png){:class="img"}
*Figure 4: Life expectancy at birth gap between genders*

Differences in mortality can also be shown by looking at the ratio between female and male mortality rates. This statistic has been used as it's fairly easy to visualise across ages, compared to other options. The ratio is calculated by taking the female mortality rate at each 1 year age step (known as mx<sub>f</sub>) and dividing this difference by the male mx<sub>m</sub>. This is visualised below in Figure 5. (Note that this graph is based on a similar one from Scholey & Willekens, 2017). 


![](/assets/images/mortality/gender_diff9.png){:class="img"}
*Figure 5: Female to male mortality ratio*

Infectious diseases/TB & Childbirth in 19th century and early 20th. (are both of these correct or not?) - https://scholar.harvard.edu/files/goldin/files/xx_xy_jhe_final.pdf. https://www.journals.uchicago.edu/doi/abs/10.1086/686035. Def TB  for that younger difference. but also childbirth may be significant for age 30-40ish

infant mortality - more male than female due to various factors e.g. male's have a lower resistance to infection and are more likely to be born prematurely and suffer from infant respiratory conditions, all of which can contribute to higher morality rates for males than females during infancy. https://www.pnas.org/doi/pdf/10.1073/pnas.0800221105

WW1 & WW2 - no citations needed.

Smoking & cardiovascular health differences - https://www.pnas.org/doi/10.1073/pnas.1421942112

Accidents, suicide & modern medicine interaction - ..........

quote some of the ratios.

explain the weird lines (to do with how data has been un-binned I presume)

### Causes

do analysis and make graphs on this if possible - maybe just show some of the more interesting causes e.g. cancer, tb & other infections, cardiovascular health.

note differences between thsi data (only civilians, no war deaths included. only from 1900 onwards.)


### References

Schöley, J. (2016). The Human Mortality Explorer (website). https://jschoeley.shinyapps.io/hmdexp/

Schöley, J. (2016). The Human Mortality Explorer (paper). https://paa.confex.com/paa/2016/mediafile/ExtendedAbstract/Paper6383/3138944_schoeley-2016-hmd_explorer.pdf

Schöley, J., & Willekens, F. (2017). Visualizing compositional data on the Lexis surface. Demographic Research, 36, 627-658. https://www.demographic-research.org/volumes/vol36/21/36-21.pdf