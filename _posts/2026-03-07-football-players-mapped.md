---
layout: post-2
title: Football Players, Mapped
description: Football Players, Mapped
summary: Visualising football through data
comments: true
tags: [Python, Affinity Designer, Webscraping]
published: true
image: /assets/images/industries-of-employment/post_image3.png
---

This project was inspired by a talk I attended about dimensionality reduction & clustering models being applied to environmental science. I was inspired to do a bit of a similar analysis myself. Alongside this, I have been interested in using football statistics in a project for a while now, the outcome of these two ideas being this post.

![](/assets/images/industries-of-employment/Industry-treemap-image.png){:class="img"}


### Data Sources & Scraping

The data itself was sourced from [FBref](https://fbref.com/) and scraped using a script written in Python. Across various leagues, FBref holds (well actually FBref held - we will get to this later) season-long statistics for every player of each team. These stats are broken down into a number of categories including:

- Standard stats
- Defense
- Passing
- Pass Types
- Possession
- Shooting
etc. etc.

Data for each player was displayed in an html table for each category. To scrape data across multiple leagues, seasons & tables we can change the web address to navigate to the correct table. E.g. for shooting stats for the premier league in the 2024-25 season the address would be: https://fbref.com/en/comps/9/2024-2025/shooting/2024-2025-Premier-League-Stats.

Data was gathered for all the players in the top 5 European Leagues from the 2020-21 season to the 2024-25 season.

Unfortunately, due to recent disagreements between FBref and Opta (the provider of most of their detailed football stats), a large amount of FBref's more interesting data is now not available anymore, which is a shame, particularly as I wanted to expand this analysis to include additional seasons and maybe even some of the other european leagues (e.g. Primeira Liga & Eredivisie).

### Methodology

insert methodology here

![](/assets/images/football-players-mapped/correlation-map.png){:class="img-somewhat-large-r"}
*Figure 1: Correlation between variables*

### Mapping Players

insert stuff here

![](/assets/images/football-players-mapped/player-map.png){:class="img-somewhat-large-r"}
*Figure 1: Football Player Map*

![](/assets/images/football-players-mapped/players-map-by-vars.png){:class="img-somewhat-large-r"}
*Figure 1: Players by Selected Statistics*

### Final Thoughts

insert thoughts here - if i have some