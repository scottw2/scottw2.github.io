---
layout: post
title: UK MP Twitter Network Analysis
description: UK MP Twitter Network Analysis
summary: UK MP Twitter Network Analysis
comments: true
tags: [R, Python]
---


## Introduction

In recent years, Twitter has become increasingly prominent in politics, not least due to ex-US President Donald Trump's questionable use of the platform. But across the pond in the UK, politicians' Twitter presences have been gradually growing over the years, as more MPs (and their teams) get online and start tweeting. Nowadays, with the majority of UK MPs on Twitter, there is an opportunity to gain insight into a number of areas, including MPs' networks, political beliefs and public appeal. This insight can be gleamed from analysing MPs' behaviour on the social network; from what they tweet, who they retweet, who they follow, who follows them etc...

The area I would like to focus on in this blog post is the parliamentary twitter network as there is not a particularly large amount of research around this. A few previous reports and articles have shown than UK MPs generally tend to cluster together within their own parties, with regard to following relationships and also re-tweet networks (McLoughlin et al., 2019), (Sleeman, 2015), (Weaver et al., 2018). Although, events like the EU referendum have lead to more cross-party interaction in terms of at least tweeting behaviour (Weaver et al., 2018). However, most of this research is a number of years old and doesn't really reflect the current parliament since the 2019 election. Moreover, the follower-following relationships of smaller parties (e.g. Lib Dems, SDLP, DUP) have not been looked at individually, as well as the within-party follower-following networks. So, in this post I am going to look at the follower-following relationships between UK MPs, with a focus on smaller parties' overall networks and also on the within-party networks of the Labour and Conservative parties.


## Data

The data was gathered in February 2021 from Twitter's API, using the Tweepy package in Python (as the data is from February, it doesn't take into account any changes since then, e.g. Neale Hanvey &amp; Kenny MacAskill defecting from the SNP to the Alba party). I downloaded a spreadsheet from https://www.politics-social.com/ which contained each MP's Twitter name, their party and their constituency. I then queried the API using Python to return a list of who each MP followed, along with their bio, follower count, like count, status count and a few other metrics. I ran into a few issues, e.g. some MPs had deleted their twitter accounts or had private profiles so I could not view their following list - so I removed those MPs from the dataset. As Twitter's free API has limits on how much data you can download in a given period, it took over 10 hours for all the data to be collected. I then did a bit of data manipulation in Python and R to get the data into the correct format for analysis and visualisation. <a href="https://github.com/scottw2/UKMPsTwitter">Python and R code available here</a>.


## Outline of MP Follower-Following Relationships

In Table 1, I have arranged a number of summary statistics for each party. I have used median and Interquartile range (IQR) stats as there are a lot of outliers and the data is not normally distributed - you can see the distribution of the number of MP Followers for all parliamentarians in Figure 1. As previous research has shown, generally MPs' following-followers relationships tend to mostly be to their own parties. This leads to the average MP followers statistic mostly reflecting the number of MPs on twitter for each party, although this relationship doesn't really hold for some of the very small parties (see the below table). However, while the Conservatives have on average more MP followers (i.e. followers who are MPs), they actually have less median total followers than most other parties, including Labour and the SNP. The Green Party has the 4th highest average MP followers and by far the most average total followers, but that is obviously due to there being only one (popular) Green MP - Caroline Lucas. The SNP has a modest median total followers relative to the Tories, Labour and the Lib Dems, possibly reflecting the geographic focus of the party. The Lib Dems have quite a high median total followers and low median MP followers. The other minor parties have fairly similar total followers and MP follower counts, apart from Sinn Féin, who have a relatively low average MP followers and high median total followers, and the SDLP, who have very high values for both stats.

![](/assets/images/uk-mp-twitter-network-analysis/table1.png)
*Table 1: Summary of parties' twitter followings*

Additionally, the Tories and Labour have quite a high variability of total followers, as measured by IQR, compared to other parties. Table 1 also shows the MPs from each party with the highest MP and total followers. For example, looking at Labour, Keir Starmer has the most MP followers, but with just over 1 million total followers, he trails ex-leader Jeremy Corbyn by a wide margin.

![](/assets/images/uk-mp-twitter-network-analysis/figure1.png)
*Figure 1: Distribution of MP Followers by Party*

Furthermore, ranking MPs by their number of MP followers can show some interesting results (see Table 2 below). Firstly, the majority of the MPs most followed by other MPs are Tories, with senior leadership and ex-leadership figures taking the top spots of the ranking. The Speaker, Lindsay Hoyle, however, comes in 3rd, reflecting his apolitical role in parliament. The only other non-Tory MPs in the top 25 are three Labour MPs - Keir Starmer, Ed Miliband and Wes Streeting.

![](/assets/images/uk-mp-twitter-network-analysis/table2.png)
*Table 2: MPs followed by the most other MPs*

One relationship, which I mentioned earlier and would like to expand on, is that while the Tories do on average have more MP followers than their Labour counterparts, Labour MPs on average have more total followers. This is visualised in Figure 2 (below). This seems to show that although the Conservatives are more linked to one another in terms of following relationships, they actually have a harder time getting follows from the general public compared to Labour. I suspect this is due to Twitter having a relatively left-wing user-base, combined with Labour MPs possibly having a stronger online presence. The distribution of MPs from other parties is also visible in the figure, with most of them clustered in the left hand side of the charts.

<div style="margin-left: -250px;
margin-right: -250px;"><iframe
     src="https://scottw2.github.io/UKMPsTwitter/LabourNetwork/" 
    height = 800px width = 1250px
      
></iframe> </div>
