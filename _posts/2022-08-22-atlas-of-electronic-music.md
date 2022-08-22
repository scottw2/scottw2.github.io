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

The idea of this projects stemmed from wanitng to do something with the spotify API and wanting to make a network visualisation having seen some really cool ones recently (see: https://www.barabasilab.com/art/works for example).


### Methodology



The data gathering process was very iterative. I stated by creating a list of various electronic artists from different subgenres and then finding their related artists. This gave me a larger list of artists and I then searched for the related artsits of artists on this list and so on for a few more iterations. The downside of this method is that is often pulled through artists that were not electronic but from literally every other genre - so I had to manually search through and filter our certain genre tags and specific artists. However, sometimes filtering out genres would exclude actual electronic music artists, so I had to make sure they were included as well. This ended up being rather time consuming, but also allowed me to discover some interesting genres and artists to listen to in the future. After creating a few initial networks using this approach, I went back and added more artists to the initial artists list to bolster some subgenres that I thought were underpresented (e.g. synthpop, EBM). I also filtered out artists with less than 10,000 spotify followers and those with no genre tags, which may bias the dataset slightly but also prevented too much noise in the visualisations. Eventually, I ended up with a pretty good dataset (I think) - including over 4000 artists and over xxxx connections between these artists.

I then exported the data to Gephi and tinkered with the ForceAtlas 2 algorithm to lay out the network. The next step was to split the network into "modularity classes" (define). I then coloured the artists in the network based on the modularity class of each artist. After this, I exported the network to illustrator to work fleshing out the visualisation.

In illustrator I added some pretty titles and text and also labeled each of the modularity classes based on the overarching genres of the classes. Some classes were easy to define, being comprised of basically one genre (e.g. hardstyle, lofi, psytrance), however others were a bit more nebulous. For instance, the "experimental" group is made up of a variety of different subgenres like ambient, future garage and classic dubstep - however the artists within these subgenres in this class could broadly be defined as experimental. Some artists were also a bit out of place, e.g. EDM artists in the dubstep class, but these were mostly "fringe" artists that join multiple genres together by the other artists they are related to, so it's not really a big issue, but it is true that the class labels are not precisely correct, and are instead more-so generalisations.


### Visualisation


![](/assets/images/atlas-of-electronic-music/electronicmusicv10-01.png)


![](/assets/images/atlas-of-electronic-music/electronicmusicv12.png)

![](/assets/images/atlas-of-electronic-music/electronicmusicv13-01.png)