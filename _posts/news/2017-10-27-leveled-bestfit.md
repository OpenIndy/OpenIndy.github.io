---
layout: post
title: "OpenIndy version 0.7.0-15 online"
modified:
categories: news
excerpt:
tags: []
image:
  feature:
date: 2017-08-23T16:00:00+02:00
---

<h1>Changelog </h1>

 OpenIndy - Version build_0.7.0_15
        
<h2>        story
</h2>
<ul>
<li>implementation of leveled alignment
</li>
<li>modify column and row size for 4K displays
</li>
<li>create feature dialog now includes feature type as dialog name
</li>
<li>implemented change radius function for cylinder
</li>
<li>sort points of wighted alignment view by name
</li>
<li>transformation parameter now are "used" by default
</li>
<li>updated unit of change radius function
</li>
</ul>
    
<h2>        task
</h2>
<ul>
<li>Featuredialog is no longer closing when an error occurs
</li>
<li>implement temperature compensation in all alignments and bestfits
</li>
<li>automatization of "Datum- transformation"
</li>
</ul>
    
<h2>        bug
</h2>
<ul>
<li>fix all "ok" and "cancel" buttons in the dialogs
</li>
<li> fixed "used" Attribute is not show, if the observation is not solved (feature property dialog)
</li>
<li>BestFitPointinPlane now loads all parameters if you load an old job
</li>
<li>fixed bug in OriginPointPoint
</li>
<li>remove observations now has a request, if you really want to remove the observations
</li>
</ul>


To improve the usability, the transformation parameters were changed. By default a new transformation parameter is now set to "used". If the same transformation already exists, an dialog appears and notifies the user for this. The "datum transformation" attribute is now handled internal and automatically. The user does not have to set this attribute anymore.
A niew function is now implemented, that makes and leveled alignment (BestFit, or single informations of the points). For this you have to measure the level with your system.
All alignments and Bestfits now include a temperature compensation. Calculated by reference, current temperature and the expansion coefficient of the specified material.
More changes see above in the changelog.