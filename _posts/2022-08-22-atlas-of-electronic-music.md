---
layout: post-2
title: Atlas of Electronic Music
description: Atlas of Electronic Music
summary: Over 5000 electronic artists mapped by their Spotify listeners.
comments: true
tags: [Python, Gephi]
published: true
image: /assets/images/atlas-of-electronic-music/post_image.png
---

The idea for this project stemmed from wanting to do something with the spotify API and to make a network visualisation having seen some really nice ones recently ([see here](https://www.barabasilab.com/art/works) for an example). Making a network graph of spotify data was not particularly innovative, as there are a number of examples online already (see [here](https://medium.com/analytics-vidhya/what-kind-of-music-do-you-listen-to-exploring-the-network-of-spotifys-genres-56d188201a07), [here](https://erdavis.com/2019/03/01/mapping-the-metalverse/) and [also here](https://wearebumper.com/blog/2022/08/22/spotify-episode-recommendation-algorithm/)), but I had not seen this idea applied to electronic music so I thought it would be a good excuse to make a few network graphs. 

![](/assets/images/atlas-of-electronic-music/atlasphotoshop2.png)

### Data

The data gathering process was rather iterative and required quite a bit of manual effort. I started by creating a list of various electronic artists from different subgenres and then finding each of their related artists using the spotipy library in python. This gave me a longer list of artists and I then searched for the related artists of artists on this list and so on for a few more iterations. 

The downside of this method was that it often pulled through artists that were not electronic but from literally every other genre - so I had to manually search through and filter our certain genre tags and specific artists. However, sometimes filtering out genres would exclude actual electronic artists, so I had to make sure they were included as well. This ended up being rather time consuming, but also allowed me to discover some interesting genres and artists to listen to in the future. I also filtered out artists with less than 10,000 spotify followers and those with no genre tags, which may have biased the dataset slightly but also prevented too much noise in the visualisations. After creating a few initial networks using this approach, I went back and added more artists to the initial artist list to bolster some subgenres that I thought were under-represented (e.g. synthpop, EBM) and reran the process.

One major issue with using Spotify data is it only represents what Spotify's users listen to and of course only has listening data from at most the last 16 years (Spotify was founded in 2006). Additionally, some artists' discographies are not available on Spotify. Because of this, a lot of artists who were at one time popular and are regarded as important in the history of electronic music are not represented very well in the dataset e.g. Klaus Schulze, Karlheinz Stockhausen, Derrick May, Juan Atkins. So this project would be better titled *"Atlas of electronic music - according to Spotify"*.

### Visualisation

The data was visualised using Gephi. I used a type of graph called a force-directed-graph, employing the ForceAtlas 2 algorithm. To add a splash of colour to the visualisation I used a community detection algorithm. This works by dividing the network into "modularity classes" - groups that generally have denser connections to nodes within the same modularity class than to nodes within other classes. Each colour in the network represents a different modularity class. 

![](/assets/images/atlas-of-electronic-music/networkiterationsv2.png)

I labelled each of the modularity class groups based on their overarching genres. Some groups were easy to define, being comprised of basically one genre (e.g. hardstyle, lofi, psytrance), however others were a bit more nebulous. For instance, the "experimental" group is made up of a variety of different subgenres like ambient, future garage and classic dubstep - however the artists within these subgenres could broadly be defined as experimental. Some artists were also a bit out of place, e.g. EDM artists in the dubstep group. These were mostly "fringe" artists that join multiple groups together by the other artists they are related to, so it's not really a big issue, but it is true that the sub-genre labels are not precisely correct, and are instead more-so generalisations. Part of the reason for this may be due to the "playlist culture" of spotify which has possibly made a clear genre classification of music somewhat redundant - as it instead allows people to group music in ways beyond a standard genre taxonomy. 

The network went through a number of different versions (see above) but I eventually ended up with a pretty good dataset and network (I think) - including just over 5000 artists.

See the end product below:  
&nbsp;  

![](/assets/images/atlas-of-electronic-music/electronicmusicv48.png){:class="img-large"}

<!---
It's interesting to see the different shapes of each sub-genre. Some, like Drum and Bass are very dense and connect mostly to other DnB artists. On the other hand, there are genres like Experimental, which are more dispersed (likely as Experimental includes various "experimental" sub-genres e.g. classic dubstep, ambient). Some sub-genres are both dispersed but have multiple dense clusters e.g. Complextro/Future Bass. ..................

It's not surprising that some of the most central sub-genres to the network are the house related sub-genres, as many types of electronic music have their roots in house music or have been influenced by house.

As mentioned earlier, some of the most influential electronic artists are not very well represented in this dataset due to the data coming from Spotify. A good example of this is how Synthpop is very xxxxxxx from the network, floating off on it's own at the bottom. .................

Newer genres generally close and interconnected. (lofi, hyperpop, future funk, phonk, synthwave)

A lot of interaction between certain groups of sub-genres, usually fairly self explanatory e.g. Dubstep & Complextro/Future Bass, House, Classic House and Tech House, Trace & Eurodance.

--->
### Final Thoughts

This visualisation took quite a while to make, with a lot of back and forth required before I was happy with it, and while it's not a perfect representation of the universe of electronic music, I think it still turned out pretty well.
