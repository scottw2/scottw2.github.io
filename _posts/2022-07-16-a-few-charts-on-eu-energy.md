---
layout: post
title: A Few Charts on EU Energy
description: A Few Charts on EU Energy
summary: A Few Charts on EU Energy
comments: true
tags: [R]
published: true
---

### Introduction

<!---
add in EU27 into each grid - either top right or bottom left. Perhaps edit the grid to add in for each chart, instead of doing in illustrator. so some overall EU comments can be made.
--->

The motivation for this post was to create some minimalist visualisations that tell a bit of a story. I thought energy supplies in the EU would be an interesting topic as I wanted to do something somewhat geographical and topical.

![](/assets/images/a-few-charts-on-eu-energy/collages1-02-01.png)

{::options parse_block_html="true" /} 

<details><summary markdown="span"> A Quite Long Note on Methodology and Definitions </summary>

The majority of the data used here is from the EU's energy balances on Eurostat. While Eurostat's energy data has good coverage, it isn't initially intuitive to understand. Eurostat provide a number of measures of energy supply and consumption at different stages of the energy transformation and consumption process. There are a variety of measures of production and primary energy consumption, notably, Total Energy Supply (TES), which measures the total amount of energy needed to satisfy all domestic energy needs for a country, including losses and consumption from energy transformation, distribution and transmission. (energy from primary production + imports - exports + recovered/recycled products + stock changes - international maritime bunkers & aviation). There are also a couple of other definition of primary energy consumption e.g. Gross Available Energy (GAE) & Gross Inland Energy Consumption (GIC). The differences from TES are that GAE includes both international maritime bunkers and aviation and GIC included international aviation, and thus both include some energy not technically used for each country's domestic energy needs - therefore I felt TES was a better measure to use to show each country's energy usage. See [here](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Energy_balance_-_new_methodology) for extra information on Eurostat's energy balance methodology.


Ideally though I would want to use statistics of final energy consumption (i.e. energy balances after losses from transformation, distribution and transmission). However, the final energy consumption stats supplied by Eurostat don't specify the original source (e.g. nuclear, renewables) - as they break down energy by it's final form (e.g. electricity, gas etc...), so for example, you cannot then say what % of energy comes from nuclear sources and the % of energy from renewables ends up being vastly underestimated as a lot of this is counted as electricity or heat. Therefore, I used Total Energy Supply here, as it captures energy supply by it's original source.

Additionally, secondary energy products (e.g. electricity and heat), can sometimes have negative Total Energy Supplies for countries. This is because only trade + stock changes are recorded for secondary products as they are produced from primary energy sources (e.g. coal, renewables) during the energy transformation process. This is problematic as 1) the negative values generally indicate a net export of a secondary product and 2) it ruins the visualisations. In an ideal world we could account for these negative values in terms of the primary energy products that are used in producing the secondary products, but it doesn't seem possible to do that with the available data. That leaves us with two approaches to dealing with this: to either exclude secondary products entirely or to just exclude them when they are negative. I decided to go with the second approach as otherwise a sizeable chunk of the energy supply of some nations would be missing. The downside to doing this though is that for nations with negative values there is now technically a small discrepancy as there is energy being produced but not accounted for - however this has only a minimal impact on the actual visualisations here (where there are negative values they are generally below 1% of the Total Energy Supply). This appears to be a similar approach to figure 6 [here](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Energy_statistics_-_an_overview).

Also note that the figures for renewables here use a slightly different definition than the figures that the EU base their renewables targets on. For their targets they look at "Gross Final Consumption of Energy" - which is final energy consumption (energy used in industry, transport, households... ) including electricity and heat losses from distribution and transmission, but excluding energy consumption and losses from transformation. It is also a definition that doesn't appear in the EU's energy balance data, which is a bit annoying. Additionally, some biofuels are not included if they don't meet certain sustainability criteria, wind and hydro power have to apparently be normalised and there are some other technical differences from other metrics. The exact differences of these details are not particularly clear e.g. it's not very clear what biofuels are included and how wind and hydro are normalised. Finally, the figures given for this metric are only the % share of renewables in the energy mix and don't break this down by the type of renewable energy (e.g. wind, solar). So because of this and to keep the analysis consistent with the rests of the data presented here, I have opted to look at renewables in the Total Energy Supply. See [this page](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Calculation_methodologies_for_the_share_of_renewables_in_energy_consumption#Definition_of_the_primary_energy_content_of_fuels) for more details on the differences between renewable energy definitions.

<!---
The data for gas sources does not come from Eurostat as the Eurostat energy imports data doesn't properly take into account energy transfers (e.g. when some countries import more than 100% of their supply from Russia and then export some of this to other nations). Instead, this data comes from ACER - The EU Agency for the Cooperation of Energy Regulators, which I believe shows the original source of each EU country's gas supply (although I cannot find details of the precise methodology used to calculate this).


The data for wind and solar power plants is from GlobalEnergyMonitor's wind and solar plant databases. These seem to be the most up-to-date freely available renewable power plant databases with data for when each power plant started operating (around 90% of plants have operating date info). Note that this data does not include smaller power plants with under 10MWs of capacity for wind and under 20MWs for solar - which may disproportionately exclude power plants in smaller nations e.g. Cyprus, Malta. The World Resource Institute also has [another database](https://blog.resourcewatch.org/2019/11/13/this-map-shows-29000-of-the-worlds-power-plants/) of power plants, which shows those with lower MW capacities.
--->

</details>
<br/>

{::options parse_block_html="false" /} 

### Energy Mix

The first thing we can look at is the energy mix of each nation (i.e. the energy supply broken down by energy source). Figure 1 shows the supply by each source as a percentage of the total energy supply for EU nations in 2020 (For a definition of the total energy supply see the note on methodology and definitions above).

![](/assets/images/a-few-charts-on-eu-energy/energy-mix-fonts-2020-flags6-01.png)*Figure 1: Energy Mix in the EU*

For most EU countries, the majority of their energy supply comes from fossil fuels, but there is still quite a wide variation in energy mixes across the EU. For example, a number of nations are still relatively reliant on coal power (Poland, Bulgaria, Czechia, Germany). Others have over 50% of their energy supply originating from Oil & Petroleum (Estonia, Cyprus, Luxembourg). In the case of Estonia this is due to their domestic shale mining operations. Contrastingly, there are nations that source a large amount of energy from renewables (Sweden, Finland, Latvia). You can also see other nations with a lot of nuclear in their energy mixes (France, Bulgaria, Slovenia, Slovakia). 

Figure 2 shows how each country's energy mixes have changed over time, between 1990 and 2000. 

![](/assets/images/a-few-charts-on-eu-energy/energy-mix-fonts-12-01.png)
*Figure 2: The EU's Changing Energy Supply*

In basically every nation we can see the decline of fossil fuels as renewable adoption has increased. This is particularly the case with coal, which is being broadly phased out across the bloc. There has however been an increase in energy derived from natural gas in quite a few states (e.g. Spain, Germany, Ireland, Belgium) - partly to substitute for lower coal/oil & petroleum usage.

The percentage of energy from nuclear power has been fairly consistent over time in most nations that utilise nuclear power (e.g. in France, Bulgaria, Hungary). In some other countries nuclear has become more important (Slovakia and Czechia), while in Spain and Belgium the opposite trend can be seen. Lithuania has a very unique graph, with nuclear disappearing entirely from their energy mix in 2009. This was due to the shutdown of the last active reactor at the Ignalina Nuclear powerplant. This was an old soviet plant and had a similar design to the one at Chernobyl. Of particular concern, the plant did not have a containment building to prevent radiation leaks in the event of emergencies, which made it rather dangerous to continue running. As part of Lithuania's accession to the EU, it was agreed in 1999 that the plant would be eventually wound down because of the risks posed by it.

### Renewables

To look in more detail at the rise of renewable energy in the EU, we can see how the percentage of energy coming from renewable sources between 1990 and 2020 has changed in Figure 3 (note that the definition used here differs from the definition the EU uses for setting renewables targets - see methodology note). 

In every EU country, the percentage of energy sourced from renewables has increased, but some states have performed better than others. Sweden currently leads the way, with 52% of their energy supply from renewables, followed by Denmark and Finland. The largest percentage change was in Denmark - 6% in 1990 to 40% in 2020. Additionally, quite a number of EU countries started with less than 3% of their energy coming from renewables sources, but now generally source more than 10% of their energy from renewables (e.g. Poland, Lithuania and Germany).

![](/assets/images/a-few-charts-on-eu-energy/ren-line08-01.png)
*Figure 3: Renewables in the Mix*

Figure 4 also shows the breakdown of renewables energy by source in each country.

![](/assets/images/a-few-charts-on-eu-energy/ren-tree-facet7-01.png)
*Figure 4: Renewable Energy Mix in the EU*

 In a lot of countries renewables energy is dominated by solid biofuels (Poland, Latvia, Finland), whereas others have a more diverse supply (Germany, Italy, Spain, France). 
 
 It's also not surprising to see a low % of solar in Nordic countries (e.g. Sweden, Finland), where they only get about 6 hours of sunlight in the winter, compared to sunnier more solar-panel-friendly Southern European Nations (Spain, Greece, Cyprus). 

Italy also has the largest share of geothermal in it's renewable energy mix (in fact Italy's geothermal energy supply is more than all other countries combined), while Ireland has the largest share and majority of it's renewable energy coming from wind. Cyprus has the highest share of solar, and similarly Slovenia has the highest for hydroelectric, Luxembourg for liquid biofuels and Germany for biogas. 

### Final thoughts

It was interesting to make these charts and investigate the differences in EU countries' energy supplies. However, Eurostat really didn't make it easy to understand and analyse the data, especially as I don't have a background in energy data - but because of this I also learned a lot about this area which is always nice.


<!---
Figure x shows the growth of the number of wind and solar power plants in Europe from 2000 to 2020. This chart shows the smaller installed capacity of solar compared to wind as well as the differences in distribution of wind and solar power plants (e.g Sweden & Finland have a lot of wind plants but no solar plants or how Spanish wind plants are mostly in the north of the country and solar plants in the south). It also shows that wind power plants generally started operating earlier than solar, due to technology differences (this might also be partly because of the higher MW cutoff point in the solar database).

#![](/assets/images/a-few-charts-on-eu-energy/ren-ws-map4-01.png)
#*Figure 5: The Growth of Solar and Wind Power*

### Russian Imports

The EU's dependency on Russian energy imports is also interesting to consider as this has been brought into the news again by the Russia-Ukraine conflict, which has led to skyrocketing gas prices and warnings of energy rationing across the continent later this year. Figure 7 shows the % of each country's gas coming from Russia compared to other sources, and gas as a % of TES.

Countries like Latvia, Hungary, Slovakia and Austria look to be the most dependent on russian imports as they have a high % of gas coming from Russia and relatively high % of gas in their energy mix. At the other end of the scale, nations including Denmark, Spain, Portugal and France seem relatively insulated from Russia in theory - although they can still be impacted by higher energy prices in the EU energy market from demand outpacing supply in other countries.


research this more.
https://www.cpb.nl/sites/default/files/omnidownload/CPB-Publication-Analysis-of-international-trade-sanctions-against-Russia.pdf
https://app.powerbi.com/view?r=eyJrIjoiMjJmYWQ4NjctYWIwNC00NzNjLWI5MmMtODVmOTQ0M2Q5YmI4IiwidCI6ImU2MjZkOTBjLTcwYWUtNGRmYy05NmJhLTAyZjE4Y2MwMDA3ZSIsImMiOjl9


adjust this graph sadly to only show russia and other sources - as the data is otherwise not accurate - 

--->