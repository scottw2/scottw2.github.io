---
layout: post
title: Atlas of Electronic Music
description: Atlas of Electronic Music
summary: Atlas of Electronic Music
comments: true
tags: [Python, Gephi]
published: true
---

### Introduction

The idea for this project stemmed from wanting to do something with the spotify API and to make a network visualisation having seen some really cool ones recently (see: https://www.barabasilab.com/art/works for example).

![](/assets/images/atlas-of-electronic-music/artisticimagev5.png)

### Methodology

The data gathering process was very iterative. I started by creating a list of various electronic artists from different subgenres and then finding each of their related artists using the spotipy library in python. This gave me a longer list of artists and I then searched for the related artists of artists on this list and so on for a few more iterations. 

The downside of this method is that is often pulled through artists that were not electronic but from literally every other genre - so I had to manually search through and filter our certain genre tags and specific artists. However, sometimes filtering out genres would exclude actual electronic artists, so I had to make sure they were included as well. This ended up being rather time consuming, but also allowed me to discover some interesting genres and artists to listen to in the future. I also filtered out artists with less than 10,000 spotify followers and those with no genre tags, which may bias the dataset slightly but also prevented too much noise in the visualisations. After creating a few initial networks using this approach, I went back and added more artists to the initial artist list to bolster some subgenres that I thought were under-represented (e.g. synthpop, EBM) and reran the process.

After this, I exported the data to Gephi and tinkered with the ForceAtlas 2 algorithm to lay out the network. The next step was to colour the network. This was done by using a community detection algorithm to split the network into "modularity classes". The algorithm works by dividing the network into groups that generally have denser connections to nodes within the same modularity class than to nodes within other classes. I then coloured the artists in the network based on the modularity class of each artist. The network went through a number of different versions (see below) but I eventually ended up with a pretty good dataset and network (I think) - including just over 5000 artists. Finally, I exported the network to illustrator.

![](/assets/images/atlas-of-electronic-music/networkiterationsv2.png)

In illustrator I added some pretty titles and text and also labelled each of the modularity class groups based on their overarching genres. Some groups were easy to define, being comprised of basically one genre (e.g. hardstyle, lofi, psytrance), however others were a bit more nebulous. For instance, the "experimental" group is made up of a variety of different subgenres like ambient, future garage and classic dubstep - however the artists within these subgenres could broadly be defined as experimental. Some artists were also a bit out of place, e.g. EDM artists in the dubstep group. These were mostly "fringe" artists that join multiple groups together by the other artists they are related to, so it's not really a big issue, but it is true that the sub-genre labels are not precisely correct, and are instead more-so generalisations. Part of the reason for this may be due to the "playlist culture" of spotify which has possibly made a clear genre classification of music somewhat redundant - as it instead allows people to group music in ways beyond what a standard taxonomy would allow.

### Visualisation

See below for the final chart:

![](/assets/images/atlas-of-electronic-music/electronicmusicv41.png)


### Final Thoughts

This visualisation took quite a while to make, with a lot of back and forth required before I was happy with it, but I think it turned out pretty well.
