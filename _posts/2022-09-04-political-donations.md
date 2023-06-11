---
layout: post-2
title: Political Donations
description: Political Donations
summary: Showing the flow of donations to UK political parties since 2001.
comments: true
tags: [R, Illustrator]
published: true
image: /assets/images/political-donations/post_image.png
---

In the UK, there exists a deep-rooted connection between political parties and wealthy individuals, companies and other organisations like trade unions, where interests and finance intertwine. A primary channel through which this relationship materialises is the mechanism of political *donations*, made by these groups to political parties. This data visualisation project delves into this world of political donations in the UK and aims to answer a few key questions: Which political parties have brought in the most donations over the years? How have donation flows changed over time? Who have been the main donors propping up each party? 


![](/assets/images/political-donations/politicsphotoshop2.png)

### Data

Following the Political Parties, Elections and Referendums Act 2000, the Electoral Commission was established in 2001 to regulate political finance and oversee elections in the UK. So, since 2001, all donations over certain thresholds (outlined below) have had to be reported to the Commission. This data is collated in the Commission's somewhat shoddy database of donations to British political parties, representatives and other political groups, which is the main data source used in this project. 

Focusing just on political parties, the database runs from 2001 and includes every donation (and loan) over £7,500 made to central political parties, along with donations over £1,500 made to "party sections" that are not managed by the central party. There are also some additional donations included under £1,500 as well.

For each donation, the value, donor's name and donor type are recorded (e.g. individual, company, trade union), as well as the dates the donation was offered, accepted and then reported to the Commission. The party receiving the donation is of course also included.

The data visualised here is from Quarter 1 2001 to Quarter 1 2022 (by the date the donation was accepted). Note that slightly more recent data is currently available (probably up to Q3 2022), but I haven't included it due to the time required to update the graphs and clean the additional data. 

I found that there were also some duplicate entries in the dataset. This is because around elections some donations are reported twice (due to the Electoral Commission's methodology), so these, along with returned or forfeited donations have been filtered out. Additionally, donations classed as "Public Funds" were removed, which filters out public funding for party administration costs, known as "short money". 

The donation values have also been adjusted for inflation using the Consumer Price Index (CPI) at an annual basis, to represent donations in constant £s.

### Donation Flows

The original idea for this project was to just create a steam graph showing the flow of donations over time - which is shown in Figure 1. However, I got carried away and created a couple of other visualisations.

Anyway, the flow of donations over time presents some intriguing insights. Firstly, and unsurprisingly, donations tend to peak around elections as parties build up war-chests to support their campaigns. This is most noticeable around UK general elections, but there are also smaller peaks coinciding with devolved parliament elections (most visible are the scottish parliament elections - as shown by rises in donations to the SNP) as well as pre-brexit EU parliament elections. The brexit and scottish independence referendums were also drivers of increased donations, as shown in the chart.

Another point of interest is how more recent general elections have set consecutive quarterly donation records, with the 2019 Election leading to £69mn of donations in Q3 2017. This perhaps indicates that money is playing a larger role in British politics than it used to.

There are also some other party-specific observations that are labelled on the chart itself.

&nbsp; 
![](/assets/images/political-donations/bumpchart.png){:class="img-somewhat-large-r"}
*Figure 1: Political Donations: Donations to each party over time*

### Where Donations Come From

Another thought-provoking chart is Figure 2 (below), which shows the sources of each party's donations (some of the smaller parties e.g. Brexit/Reform and UKIP are included in the "other" category here). 

There is quite a stark difference in funding sources between Labour and the Conservatives, with 68% of Labour's donations coming from trade unions - along with 99.9% of trade union donations going to Labour, compared to individuals making up 64% of the Tories' donations, and the rest coming from companies or other sources (e.g. unincorporated associations or trusts).

In fact, the Tories, Lib Dems and "Other" parties all have a similar breakdown of donations by source in percentage terms, with the majority coming from individuals, followed by companies and other sources.

&nbsp; 

![](/assets/images/political-donations/alluvial.png){:class="img-somewhat-large-r"}
*Figure 2: Donations to each party by source*

### Top Donors

I also decided to visualise the largest donors to each party, however the data quality of donor names was absolutely terrible, so extensive data cleaning was unfortunately required. For example,  one of the largest donors and main funder of UKIP, Christopher Harborne, had donations under six different names in the dataset. 

To clean this dataset I changed all names to lowercase, removed punctuation, suffixes and prefixes (e.g. mr, mrs, lord, mbe) and deleted some middle names. This improved the dataset somewhat. However, there were still quite a lot of issues due to general inconsistencies (e.g. a reid and alan reid) and grammatical errors (e.g. angelsource and anglesource). I was only really interested in large donors - say those spending over £100k, so I filtered the dataset for donors with over £10k donated and starting from the largest donors, looked for entries under other names within the dataset. I went down to those donating £55k. This was a somewhat arbitrary cut-off point but should mean that I have captured all the duplicate entries for the vast majority of those donating over 100k in total. In the case of donations coming from subsidiary companies, I generally tried to group these under one parent company (e.g. JCB Ltd. & JCB were grouped under JCB). Additionally, for trade unions, sometimes there were donations from specific "sections" of a union, which I aggregated under the main union name (e.g. Unite & Unite - Amicus section were grouped under Unite). Often this appears to have been the case where multiple unions merged to form another.

The final dataset is probably still not perfect but it is definitely a great improvement on the source data and should be reasonably accurate. 

See the top donors by party in Figure 3 below:

&nbsp;

![](/assets/images/political-donations/circles.png){:class="img-somewhat-large-r"}
*Figure 3: Top donors to each party*

It is immediately obvious that **Labour** has been primarily funded by a small number of *very generous* trade unions (Unite, GMB, Unison, USDAW, CWU) plus a few individual donors (Lord David Sainsbury, Lakshmi Mittal - unlabelled). 

Labour ranks second in terms of the total donations received from large donors, trailing the **Conservative Party**. Moreover, while the Conservatives' large donor-base is less concentrated than Labour's, there are still a number of people & companies with deep pockets (and a lot of influence in the party), for example, companies like JCB & IPGL and individuals such as Michael Farmer, David Rowland and Mick Davis. 

It also appears that a lot of the companies that have donated to political parties tend to effectively be donations made by individuals that own these companies. This is especially the case for the Tories, e.g. the Bamford family has donated £5.5mn personally and £13.6mn through their group of JCB companies (yes that JCB), while IPGL (£8.2mn donated) is the private holding company of Lord Michael Spencer, who has only donated £430k personally. Another example is Bearwood Corporate Services (£7.7mn donated), which is owned by Lord Michael Ashcroft (£1mn donated) and was [investigated by the Electoral Commission between 2009 and 2010 for not being a "proper" company and acting a proxy for Ashcroft to make donations](https://www.theguardian.com/politics/2010/mar/04/electoral-commission-lord-ashcroft-donations).

Moving on, the **Liberal Democrats** come in third in terms of total donations from big spenders and have two stand-out donors, Lord David Sainsbury (again) and the Joseph Rowntree Reform Trust. They also received £3.7mn in donations in 2005 from 5th Avenue partners, a firm setup by convicted fraudster Michael Brown, that caused [quite a scandal](https://www.theguardian.com/politics/2014/jul/17/inquiry-fraudster-michael-brown-donation-lib-dems).

The **Reform Party** (previously the **Brexit Party**) has been propped up by one Christopher Harborne, who has donated a total of £11.4mn.  Leave Means Leave, a pro-Brexit pressure group ran by the same people in charge of the Brexit Party also donated £1.1mn, alongside Jeremy Hosking, who gave £1.8mn.

The 5 largest donors to **UKIP** are all companies. Similar to the Conservatives these are however realistically donations from individuals through their companies. Highstone Group, a company controlled by Paul Sykes, donated the most with £3.0mn. Sykes has also donated £900k through another company, the Paul Sykes Group. Northern & Shell Group, publisher of the Daily Express and Star also donated £1.6mn to the party, on behalf of owner Richard Desmond. The third largest donor is well known Brexiteer Aaron Banks, who gave UKIP £1.4mn through his firm Rock Services. 

The **SNP** received £3.3mn from businessman Brian Souter, £2.8mn each from lottery winners Christine and Colin Weir as well as £1.4mn from late poet Edwin Morgan.

Out of the parties in the "Other" category, there are also a few donors worth mentioning. Firstly, the **Co-operative Party** received £15.0mn from the Co-operative group. Secondly, Jeremy Hosking effectively funded the 2020 launch of new right wing **Reclaim Party** with £2.7mn in donations. Finally, **Sinn Féin** also accepted £3.2mn in donations from a Mr William Hampton.

 Additionally, across both of the two main parties there are quite a few generous donors with knighthoods, lordships and other honours which I think is worth mentioning. Looking at the top 50 largest individual donors to the Conservative party, 20 have received knighthoods and/or been given lordships. Similarly, for the top 50 Labour party donors, 18 have been made knights of the realm or lords.

### Final Thoughts

This project shows that donations have tended to peak around elections and that more recent general elections have set consecutive quarterly donation records. Additionally, the difference in funding sources between parties is easy to see, with 68% of Labour's donations coming from trade unions and 64% of the Tories' donations coming from individuals for instance. Moreover, while the data quality of donor names was very poor, after cleaning the data it was possible to see the who the main funders of each party were. 

Overall, this project provides a glimpse into the flow of political donations in the UK, and may raise questions about the role of money in British politics.


<!---
Below I have also included an interactive table to explore the top donors. 

<div class="img-somewhat-large" style="width:125%;border:none"><iframe
     src="/assets/widgets/political-donations/table_1.html"
     width="100%" height = 750px frameBorder="0"
 ></iframe>   
 </div>
--->