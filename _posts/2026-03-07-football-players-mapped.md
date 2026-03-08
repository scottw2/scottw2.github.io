---
layout: post-2-lg
title: Football Players, Mapped
description: Football Players, Mapped
summary: Visualising football through data
comments: true
tags: [Python, Affinity Designer, Webscraping]
published: true
image: /assets/images/football-players-mapped/post-image2.png
---

This project was inspired by a talk I attended about dimensionality reduction & clustering models being applied to environmental science. Alongside this, I have been interested in using football statistics in a project for a while now, the outcome of these two ideas being this post.

The overall plan was to see if I could create some visualisations that use variables describing football players' performance to cluster them into groups based on the positions they each play e.g. defender, attacker, midfielder.

![](/assets/images/football-players-mapped/post-header-image.png){:class="img"}

### Data Sources & Scraping

The data itself was sourced from [FBref](https://fbref.com/) and scraped using a script written in Python. Across various football leagues (e.g. Premier League, La Liga), FBref holds (well actually FBref held - we will get to this later) season-long statistics for every player of each team. These stats are broken down into a number of categories including:

- Standard stats
- Defence
- Passing
- Pass Types
- Possession
- Shooting
etc. etc.

Data for each player was available in an html table for each category. To scrape data across multiple leagues, seasons & tables we can change the web address to navigate to the correct table. E.g. for shooting stats for the premier league in the 2024-25 season the address would be: https://fbref.com/en/comps/9/2024-2025/shooting/2024-2025-Premier-League-Stats.

Data was gathered for all the players in the top 5 European Leagues from the 2020-21 season to the 2024-25 season. I used the Selenium python library's headless browsers to automatically navigate through each page and scrape the relevant data. This also circumvented FBref's cloudflare scraping restrictions that prevented simpler scraping approaches e.g. using requests & beautifulsoup.

Unfortunately, due to recent disagreements between FBref and Opta (the provider of most of their detailed football stats), a large amount of FBref's more interesting stats are now not available anymore, which is a shame, particularly as I wanted to expand this analysis to include additional seasons and maybe even some of the other european leagues (e.g. Primeira Liga & Eredivisie).

### Data Wrangling & Processing

After downloading our data, I combined this into one table and tidied it up, ready for running the dimensionality reduction & clustering models.

Data was cleaned using the following steps:

NA values replaced with 0, as these are not referring to missing data but generally where players don't actually have stats for those specific variables (e.g. defenders with no goals scored or shots on target or attackers with no tackles won)

Players with a low playtime were filtered out (less than 10 games - so about 30% ish of total playtime) - often players with low playtime may have better than expected stats per 90 as they come on as substitutes vs tired players and overperform compared to if they were a regular starter. 

Goalkeepers were also removed from the analysis. They behave very differently than outfield players, so most of the variables that describe their performance are not relevant to outfield players and vice-versa. I thus decided to focus only on outfield players in this analysis.

Some new variables were engineered to provide additional detail - generally around performance (which may help differentiate players based on their abilities in different facets of the game) or around positioning and actions within parts of the pitch (as this should help identify player positioning e.g. a defender will spend more of their time in the defensive 3rd of the pitch vs a midfielder or attacker)

    - Share of pass types (e.g. progressive, long, short, passes into opponent 3rd)
    - Share of tackles by part of pitch
    - Share of possession by part of pitch
    - Npxg per 90

Correlation matrices were used to identify highly correlated variables and filter down the number of variables accordingly. Figure 1 below shows the final variables and the correlation between these. You may see that some variables with very high correlation still exist, but they tended to be measuring different aspects of performance, so I opted to leave them in.

![](/assets/images/football-players-mapped/correlation-map-2.png){:class="img-somewhat-large"}
*Figure 1: Correlation between variables*

Variables were then classed into
    - summary columns (not used as part of modelling, but descriptive variables e.g. team, player name that will be useful for interpreting the analysis)
    - rate column (used in modelling but no need to normalise per 90 minute match)
    - volume columns (used in modelling, normalised per 90 to improve comparability per player)

Variables were then scaled using the StandardScaler function

### Modelling & Visualisations

 Process was to firstly use dimensionality reduction to reduce the dataset to 2 or 3 dimensions. Then use a clustering model to divide the lower dimension data into broad clusters - attempting to cluster players into their respective positions.

A few different **dimensionality reduction** models were tested, PCA, UMAP & TSNE. UMAP appeared the most effective as it was effective at identifying local structures in the data whilst retaining a good overall structure. 

The UMAP hyper parameters were tuned through trial and error, alongside the clustering model of choice to cluster the data effectively. Angular/Correlation metrics were the best for this approach. The correlation metric appeared to be the most useful metric (WHY?) - cosine wasn't far behind.

A very low min_dist combined with an average n_neighbors was the most effective at generating useful clusters. The low min_dist tends to clump points together more and the average n_neighbors provided a good balance in retaining global & local relationships in the model.

Adjusting the spread function also helped to generate interpretable clusters. Changing this between 0.75-2 (default 1) provided interesting outcomes.

After reducing the dimensions, this data was fed into a **clustering model**

Various models were tested including K means, DBScan & HDBScan.

K Means provided a very rudimentary clustering, so was discarded as an approach.

DBScan was better and generated more insightful clusters, however it struggled to break some of the larger groups of points into clusters.

HDBScan appeared to be the most effective model to identify useful clusters as it requires less assumptions about the data than K Means so was better at working with our data and was more effective than DBScan at breaking larger structures down into multiple different clusters.

HDBScan also identifies some points as "Noise" - where the model struggles to assign these to one specific cluster. We can use "soft clustering" to assign most of these points to their closest cluster. For each point, this was done by finding the cluster with the highest probability of them belonging to that specific cluster other than the noise cluster and if this probability was >= 25%, adding them to the respective cluster. This brings down the number of noise points significantly but doesn't fully remove the really noisy points. The remaining noise is shown as the "various" category in Figure 2.

#### Visualisation
The final clustering model breaks the players down into these clusters and is visualised in Figure 2 below:
- Centre backs
- Full back/Wing backs
- Defensive & Central Midfielders
- Attacking Midfielders/Wingers
- Forwards

Note that the **axes** (or dimensions) in Figures 2 & 3 are not really meaningful as they are the combination of 44 different variables via the dimensionality reduction applied earlier. The purpose of doing this is to summarise all the variables into 2 dimensions, to allow us to more easily interpret and visualise our data (as well as improve the performance of the clustering model)

The approach is not perfect at putting players into their correct group based on their listed position - but as it is using their underlying data is potentially implies that those players actually fit a different archetype than their listed position - or it implies that our approach lacks additional variables (which it probably does, but the former reason still seems to apply as well!)

![](/assets/images/football-players-mapped/player-map-2.png){:class="img-somewhat-large"}
*Figure 2: Football Player Map*

We can see the different types of player in each cluster and also the variation with clusters by visualising different variables across the players. e.g. Touches_in_defensive_3rd_%, Crosses_per_90, Non_pen_expected_goals_per90, Take-ons_attempted_per90, Tackles_per90. This is shown here in Figure 3.

![](/assets/images/football-players-mapped/players-map-by-vars-2.png){:class="img-somewhat-large"}
*Figure 3: Players by Selected Statistics*

Add some description around what we can see in this visualisation.

### Final Thoughts

insert thoughts here - if i have some