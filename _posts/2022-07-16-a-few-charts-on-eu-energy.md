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

### A Quite Long Note on Methodology and Definitions

The majority of the data used here is from the EU's energy balances on Eurostat. While Eurostat's energy data has good coverage, it isn't initially intuitive to understand. Eurostat provide a number of measures of energy supply and consumption at different stages of the energy transformation and consumption process. There are a variety of measures of production and primary energy consumption, notably, Total Energy Supply (TES), which measures the total amount of energy needed to satisfy all domestic energy needs for a country, including losses and consumption from energy transformation, distribution and transmission. (energy from primary production + imports - exports + recovered/recycled products + stock changes - international maritime bunkers & aviation). There are also a couple of other definition of primary energy consumption e.g. Gross Available Energy (GAE) & Gross Inland Energy Consumption (GIC). The differences from TES are that GAE includes both international maritime bunkers and aviation and GIC included international aviation, and thus both include some energy not technically used for each country's domestic energy needs - therefore I felt TES was a better measure to use to show each country's energy usage. See [here](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Energy_balance_-_new_methodology) for extra information on Eurostat's energy balance methodology.

<!---
insert sankey graph of the EU energy balance flow.
--->

Ideally though I would want to use statistics of final energy consumption (i.e. energy balances after losses from transformation, distribution and transmission). However, the final energy consumption stats supplied by Eurostat don't specify the original source (e.g. nuclear, renewables) - as they break down energy by it's final form (e.g. electricity, gas etc...), so for example, you cannot then say what % of energy comes from nuclear sources and the % of energy from renewables ends up being vastly underestimated as a lot of this is counted as electricity or heat. Therefore, I used Total Energy Supply here, as it captures energy supply by it's original source.

Also note that the figures for renewables here use a slightly different definition than the figures that the EU base their renewables targets on. For their targets they look at "Gross Final Consumption of Energy" - which is final energy consmption (energy used in industry, transport, households... ) including electricity and heat losses from distribution and transmission, but excluding energy consumption and losses from transformation. It is also a definition that doesn't appear in the EU's energy balance data, which is a bit annoying. Additionally, some biofuels are not included if they don't meet certain sustainability criteria, wind and hydro power have to apparently be normalised and there are some other technical differences from other metrics. The exact differences of these details are not particuarly clear e.g. it's not very clear what biofuels are included and how wind and hydro are normalised. Finally, the figures given for this metric are only the % share of renewables in the energy mix and don't break this down by the type of renewable energy (e.g. wind, solar). So because of this and to keep the analysis consistent with the rests of the data presented here, I have opted to look at renewables in the Total Energy Supply. See [this page](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Calculation_methodologies_for_the_share_of_renewables_in_energy_consumption#Definition_of_the_primary_energy_content_of_fuels) for more details on the differences between renewable energy definitions.

<!---
The data for gas sources does not come from Eurostat as the Eurostat energy imports data doesn't properly take into account energy transfers (e.g. when some countries import more than 100% of their supply from Russia and then export some of this to other nations). Instead, this data comes from ACER - The EU Agency for the Cooperation of Energy Regulators, which I believe shows the original source of each EU country's gas supply (although I cannot find details of the precise methodology used to calculate this).
--->

The data for wind and solar power plants is from GlobalEnergyMonitor's wind and solar plant databases. These seem to be the most up-to-date freely available renewable power plant databases with data for when each power plant started operating (around 90% of plants have operating date info). Note that this data does not include smaller power plants with under 10MWs of capacity for wind and under 20MWs for solar - which may disproportionately exlude power plants in smaller nations e.g. Cyprus, Malta. The World Resource Insitute also has [another database](https://blog.resourcewatch.org/2019/11/13/this-map-shows-29000-of-the-worlds-power-plants/) of power plants, which shows those with lower MW capacities.

### Energy Mix

The first thing we can look at is the energy mix of each nation (i.e. the energy supply broken down by energy source). Figure 1 shows the supply by each source as a % of the total energy supply. 

Most EU countries supply the majority of their energy supply from fossil fuels, but there is still quite a wide variation in energy mixes across the EU. For example, a number of nations are still relatively reliant on coal power (Poland, Bulgaria, Czechia, Germany). Others have over 50% of their energy supply originating from Oil & Petroleum (Estonia, Cyprus, Luxembourg). In the case of Estonia this is due to their domestic shale mining operations. Contrastingly, there are nations that have a large amount of energy from renewables (Sweden, Finland, Latvia). You can also see other nations with a lot of nuclear in their energy mix, especially in Central and Eastern Europe (France, Bulgaria, Slovenia, Slovakia). 

![](/assets/images/a-few-charts-on-eu-energy/energy-mix-fonts-2020-01-pink3-01-01.png)*Figure 1: Energy Mix in the EU*

Figure 3 shows how each country's energy mixes have changed over time, between 1990 and 2000. In basically every nation we can see the decline of fossil fuels as renewable adoption has increased. There has also been an increase in energy derived from natural gas in quite a few states (e.g. Spain, Germany, Ireland, Belgium), as higher gas usage has substituted for lower coal usage as countries have phased out coal power plants. The % of energy from nuclear power has been fairly consistent over time in some nations (e.g. in France, Bulgaria,Hungary). In other countries it has grown (Slovakia and Czechia), while in states like Denmark and Belgium it has shrunk. Lithuania has a very unique graph, with nuclear disappearing entierly from their energy mix in 2009. This was due to the shutdown of the last active reactor at the Ignalina Nuclear powerplant, which was an old soviet plant and had a similar design to the one at Chernobyl. Of particular concern, the plant did not have a containment building to prevent radiation leaks in the event of emergencies, which made it rather dangerous to continue running. As part of Lithuania's accession to the EU, it was agreed in 1999 that the plant would be wound down because of the risks posed by it.

![](/assets/images/a-few-charts-on-eu-energy/energy-mix-fonts-10-01-01.png)
*Figure 2: The EU's Changing Energy Supply*

### Renewables

To look in more detail at the rise of renewable energy in the EU, we can focus on the change in % of the energy supply coming from renewables between 1990 and 2020 in Figure 4 (note that the definition used here differs from the definition the EU uses for setting renewables targets - see above). In every EU country this has increased, but some much more than others. Sweden currently leads the way, with 52% of their energy supply from renewables, followed by Denmark and Finland. Denmark also have had the largest % change - from 6% to 40%. Additionally, quite a number of EU countries started with only 1, 2 or 3% of their energy from renewables sources, but have grown these to generally the double digits (e.g. Poland, Lithuania and Germany), which is good, but still lags far behind the leading nations.

![](/assets/images/a-few-charts-on-eu-energy/ren-line04-01.png)
*Figure 3: Renewables in the Mix*

From which renewables sources is this energy coming from? Figure 6 below shows this below. This graph is sort of similar in design to Figure 2, but uses both axes to represent the % share, instead of just the x axis. 

In this graph we can also see the countries getting their renewable energy from each source. For example, we can see that a lot of countries are dominated by solid biofuels (Poland, Latvia, Finland), whereas others have a more diverse supply (Germany, Italy, Spain, France). It's also not suprising to see a low % of solar in Nordic countries (Sweden, Finland), where they only get about 6 hours of sunlight in the winter, compared to sunnier more solar-panel-friendly Southern and Central European Nations (Spain, Netherlands, Greece, Cyprus). 

Italy has the largest share of geothermal in it's renewable energy mix, while Ireland has the largest share and majority of it's renewable energy coming from wind. Cyprus has the highest share of solar, and similarly Slovenia the higest for hydroelectric, Luxembourg for liquid biofuels and Germany for biogas. 

![](/assets/images/a-few-charts-on-eu-energy/ren-tree-facet4-01.png)
*Figure 4: Who Uses What Renewables*

Figure x shows the growth of the number of wind and solar power plants in Europe from 2000 to 2020. This chart shows the smaller installed capacity of solar compared to wind as well as the differences in distribution of wind and solar power plants (e.g Sweden & Finland have a lot of wind plants but no solar plants or how Spanish wind plants are mostly in the north of the country and solar plants in the south). It also shows that wind power plants generally started operating earlier than solar, due to technology differences (this might also be partly because of the higher MW cutoff point in the solar database).

![](/assets/images/a-few-charts-on-eu-energy/ren-ws-map4-01.png)
*Figure 5: The Growth of Solar and Wind Power*


<!---
### Russian Imports

The EU's dependency on Russian energy imports is also interesting to consider as this has been brought into the news again by the Russia-Ukraine conflict, which has led to skyrocketing gas prices and warnings of energy rationing across the continent later this year. Figure 7 shows the % of each country's gas coming from Russia compared to other sources, and gas as a % of TES.

Countries like Latvia, Hungary, Slovakia and Austria look to be the most dependent on russian imports as they have a high % of gas coming from Russia and relatively high % of gas in their energy mix. At the other end of the scale, nations including Denmark, Spain, Portugal and France seem relatively insulated from Russia in theory - although they can still be impacted by higher energy prices in the EU energy market from demand outpacing supply in other countries.

<!---
research this more.
https://www.cpb.nl/sites/default/files/omnidownload/CPB-Publication-Analysis-of-international-trade-sanctions-against-Russia.pdf
https://app.powerbi.com/view?r=eyJrIjoiMjJmYWQ4NjctYWIwNC00NzNjLWI5MmMtODVmOTQ0M2Q5YmI4IiwidCI6ImU2MjZkOTBjLTcwYWUtNGRmYy05NmJhLTAyZjE4Y2MwMDA3ZSIsImMiOjl9


adjust this graph sadly to only show russia and other sources - as the data is otherwise not accurate - 

![](/assets/images/a-few-charts-on-eu-energy/gas_facet1-01.png)
--->