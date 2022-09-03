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

The idea for this projects stemmed from wanting to do something with the spotify API and wanting to make a network visualisation having seen some really cool ones recently (see: https://www.barabasilab.com/art/works for example).

### Methodology

The data gathering process was very iterative. I started by creating a list of various electronic artists from different subgenres and then finding their related artists using the spotipy library in python. This gave me a larger list of artists and I then searched for the related artists of artists on this list and so on for a few more iterations. 

The downside of this method is that is often pulled through artists that were not electronic but from literally every other genre - so I had to manually search through and filter our certain genre tags and specific artists. However, sometimes filtering out genres would exclude actual electronic artists, so I had to make sure they were included as well. This ended up being rather time consuming, but also allowed me to discover some interesting genres and artists to listen to in the future. I also filtered out artists with less than 10,000 spotify followers and those with no genre tags, which may bias the dataset slightly but also prevented too much noise in the visualisations. After creating a few initial networks using this approach, I went back and added more artists to the initial artists list to bolster some subgenres that I thought were under-represented (e.g. synthpop, EBM).

I then exported the data to Gephi and tinkered with the ForceAtlas 2 algorithm to lay out the network. The next step was to colour the network. This was done by using a community detection algorithm to split the network into "modularity classes". This algorithm works by dividing the network into groups that generally have denser connections to nodes within the same class that to nodes within other classes. I then coloured the artists in the network based on the modularity class of each artist. The network went through a number of different versions (see below) but eventually, I ended up with a pretty good dataset and network (I think) - including just over 5000 artists. After this, I exported the network to illustrator to work fleshing out the visualisation.

![](/assets/images/atlas-of-electronic-music/networkiterationsv1.png)

In illustrator I added some pretty titles and text and also labelled each of the modularity classes based on the overarching genres of the classes. Some classes were easy to define, being comprised of basically one genre (e.g. hardstyle, lofi, psytrance), however others were a bit more nebulous. For instance, the "experimental" group is made up of a variety of different subgenres like ambient, future garage and classic dubstep - however the artists within these subgenres in this class could broadly be defined as experimental. Some artists were also a bit out of place, e.g. EDM artists in the dubstep class, but these were mostly "fringe" artists that join multiple genres together by the other artists they are related to, so it's not really a big issue, but it is true that the sub-genre labels are not precisely correct, and are instead more-so generalisations. Partly the reason for this may be because the "playlist culture" of spotify has made a clear genre classification of music somewhat redundant - as this instead allows people to group music in ways beyond what a standard taxonomy would allow.

### Visualisation

See below for the final chart:

![](/assets/images/atlas-of-electronic-music/electronicmusicv41.png)


### Final Thoughts

This visualisation took quite a while to make, with a lot of back and forth required before I was happy with it, but I think it turned out pretty well.
