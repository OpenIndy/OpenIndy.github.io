---
layout: post
title: "OpenIndy version 0.8.0-16 online"
modified:
categories: news
excerpt:
tags: []
image:
  feature:
date: 2017-11-14T16:00:00+02:00
---

<h1>Changelog </h1>

 OpenIndy - Version build_0.8.0_16
        
<h2>        Story
</h2>
<ul>
<li> play sounds for successful and unsuccessful measurements
</li>
<li> open functions dialog with double click or right click on features and transformation parameters
</li>
</ul>
    
<h2>        task
</h2>
<ul>
<li> display target geometry of observations in functions dialog.
</li>
</ul>
    
<h2>        Bug
</h2>
<ul>
<li> if you change a function you can now find the observation in the station list, including its target geometry
</li>
<li> observations are now displayed in functions dialog with their ID and the targetGeometry
</li>
<li> updating bundle input-geometries for view
</li>
<li> [Modul] Robocalc, fixed function "copy nominal to actual tool"
</li>
<li> "ReferencePoint" crashes, when the reference geometry is deleted
</li>
<li> [Modul] fixed an issue calculating ABB bases
</li>
<li> fixed weighted alignment and weighted-leveled-alignment. Now checking number of needed geometries correct
</li>
<li> ChangeRadius now changes radius of circle and cylinder
</li>
</ul>

Another update to improve the usability. You can now also open the functions dialog by right clicking the feature, or by double clicking the "function" column of the feature.
Observations are now displayed with their ID and target geometry in the functions dialog (in the corresponding feature and in the list of observations of the corresponding station).
In the settings you can now select to play sounds for successful and unsuccesful measurements.

[Modul] We fixed an issue of the definition of ABB quaternions and improved the algorithm to calculate bases and tools.

By these changes it is easier to set and change functions for features and transformation parameters. If you change a function you can now find the old observations in the dialog in the list of their station.
In this version we improved the stability of weighted alignment and level-weighted alignment in connection with the changes of the function dialog and observations.
According with this changes the view of transformation parameters changed. The order of the attributes is now different. The solved and used attribute are now in the beginning of the parameters to have a better overview of the important settings, like these two and the start and destination system.