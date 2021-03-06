---
layout: post
title: "OpenIndy version 0.6.0-14 online"
modified:
categories: news
excerpt:
tags: []
image:
  feature:
date: 2017-08-23T16:00:00+02:00
---

<h1>Intro to bundle adjustment </h1>
An open-source bundle adjustment is now implemented in the current version of OpenIndy.
Here you can download [OpenIndy version 0.6.0-14](https://openindy.github.io/download/).

The following blog will guide you through OpenIndy and how to use the bundle adjustment.
To demonstrate a use-case where the bundle adjustment is useful, we will check if a tube is leveled.

<h1>Preparation</h1>

To check if the tube is leveled, we will measure a circle on both sides of the tube. To do so, we need to link our two lasertracker (LT) stations, one on each side. We solve this step by sticking 4 common points around our tube. We measure them from both stations and run a bundle adjustment to link our stations and all the measured data.

<figure>
	<p align="middle"><a href="/images/news/bundle/overview compoints and tube.jpg"><img src="/images/news/bundle/overview compoints and tube.jpg"></a> </p>
	<p align="middle"><i>overview</i></p>
</figure>

As second step of preparation you connect the sensor via the menu "Station -> set sensor" and choose your tracker. Also you can create a new configuration with your own IP- address. The pre-defined configurations all include some IP- addresses for tracker.
If you chose "set", you will connect to the sensor.

<figure>
	<p align="middle"><a href="/images/news/bundle/02_select sensor and set.png"><img src="/images/news/bundle/02_select sensor and set.png"></a> </p>
	<p align="middle"><i>set sensor</i></p>
</figure>

Last step is to pre-define all geometries that you need. First we start to define our common points. Choose "Features -> create point" and specify a name (e.g. "com01"), a group (com) and set the count to 4. It is important that you choose "common" and "actual". Common means, that this geometry is used for linking the different LT stations with the bundle adjustment. As function we choose "BestFitPoint", so all observations for this feature will be bestfitted to one point, and fast point as measurement config.
Alternatively you can create and configure the features in the toolbar on the left side of the screen.

<figure>
	<p align="middle"><a href="/images/news/bundle/05_create com point.png"><img src="/images/news/bundle/05_create com point.png"></a> </p>
	<p align="middle"><i>create common points</i></p>
</figure>

For the other geometries you choose the corresponding menu and create them the same way. Only for them you do not have to choose common.
The level plane is one special case. Here you chose "FitLevel" as function and "level" as measurement config.
By measuring this plane the tracker will get his reference to the level, that is neccessary for our superordinated coordinate system.
For all other geometries, like the points, circles etc. you should use the "fastPoint" measurement configuration.

<h1>Measure geometries</h1>

Before you start measure you should open the "sensor control pad" and run an compensation / initialization.
<figure>
	<p align="middle"><a href="/images/news/bundle/03_sensor_control_pad.png"><img src="/images/news/bundle/03_sensor_control_pad.png"></a> </p>
	<p align="middle"><i>sensor control pad</i></p>
</figure>

Afterwards, measure your common points.
To specify our coordinate system we measure a level plane to get our primary axis reference. Select the geometry from the list and press "F3" to measure. Continuing with the first circle on the tube flange. You can switch the selected feature by the arrow buttons on your keyboard or by mouse click. If you do not switch the active feature, all measurements will be made in this feature.
The current active feature is highlighted in a blue color.

<figure>
	<p align="middle"><a href="/images/news/bundle/measure circle.jpg"><img src="/images/news/bundle/measure circle.jpg"></a> </p>
	<p align="middle"><i>measure first tube flange</i></p>
</figure>

You can check all observations of the circle and of all other features by right clicking them in the table view and "show properties". In this view you can activate and deactivate single measurements to include or exclude from algorithm. In the last columns you can see the deviations from each points in x, y and z direction to the circle and the 3D distance deviation.

<figure>
	<p align="middle"><a href="/images/news/bundle/10_check_obs.png"><img src="/images/news/bundle/10_check_obs.png"></a> </p>
	<p align="middle"><i>check observations of circle</i></p>
</figure>

Now we have our level plane and the first tube flange. We need to measure the flange on the other side of the tube, what is not possible from this station.

It is necessary to put the tracker and tripod to the other side of the object and create an new station in OpenIndy. Activate this station in the menu and measure all common points also from this position. To activate a station, select it in the table view and go to the menu "station -> activate". Current active stations are highlighted with a dark grey in the tableview, whereas all other stations, that are currently not active, are highlighted in a light grey.
<br>
 You will see, in the first moment the algorithm of the point will not use all observations, because their is no relation between the first and the second station observations.

After you measured three common points, you can run the bundle for the first time.

<h1>Bundle adjustment</h1>

For this following step, go to the tab "bundle" in the OpenIndy main view.

<figure>
	<p align="middle"><a href="/images/news/bundle/14_create_bundle.png"><img src="/images/news/bundle/14_create_bundle.png"></a> </p>
	<p align="middle"><i>create bundle adjustment</i></p>
</figure>

Add a bundle to the job by clicking the green "add" button. Select it from the list and press "load" next to the selected template. This template specifies the parameters, that will be calculated internally by the bundle.<br>
This step is only neccessary to do once for all the job.
In the tab "input geometries" you can see all stations and geometries that are used to solve the bundle between these stations.

<figure>
	<p align="middle"><a href="/images/news/bundle/16_overview_bundle_input.png"><img src="/images/news/bundle/16_overview_bundle_input.png"></a> </p>
	<p align="middle"><i>bundle input</i></p>
</figure>

Press "run bundle" to calculate the bundle and create one superordinate coordinate system called "bundle". The output is transformation parameters from all included stations to the bundle coordinate system. You can find all these parameters in the tab "transformation parameters". Here you see, in our example, 2 transformations. From station1 to bundle and station2 to bundle. With these parameters we can now use and transform all observations of these stations to fit our geometries.
<br>
Switching to the tab "transformation parameters" you can see the calculated transformations. Check that alle parameters have the "used" flag (see red box in the picture), if you want to use them for transforming observations from these stations.
<figure>
	<p align="middle"><a href="/images/news/bundle/18_bundle_trafos.png"><img src="/images/news/bundle/18_bundle_trafos.png"></a> </p>
	<p align="middle"><i>bundle result</i></p>
</figure>

With our successful bundled stations, we are now able to "aim (Alt +A moves the laser beam to the selected feature position)" our other geometries that have been measured from a previous station and measure them again. Afterwards, go back to the bundle tab and press "run bundle". The bundle will be recalculated with all input geometries (including the new forth point) and the transformation parameters will change slightly.

<br>Until this step we have all our observations and measured data in one bundle coordinate system. To compare the two flanges in dependancy to our level plane, we have to construct another transformation from our observations (bundle system) to the superordinate coordinate system "PART".
To solve this, we use our circles and the plane to construct the coordinate axis and the origin.

<figure>
	<p align="middle"><a href="/images/news/bundle/26_create_trafo_bundlePart.png"><img src="/images/news/bundle/26_create_trafo_bundlePart.png"></a> </p>
	<p align="middle"><i>create transformation parameter</i></p>
</figure>

We use the function "Origin-Vector-Vector" to define our system. Origin is the center point of our first flange circle. Our primary axis (+Z) is the normal vector of our level plane and as secondary axis (+X) we use the normal vector from our first flange circle.
So we can see the deviations of the second flange circle compared to the first flange circle.
Select the new transformation parameter and go to the menu "Function -> set function". Select "origin-vector-vector" by double clicking.
Specify the axis in the first interface and then assign the geometries to the function.

<figure>
	<p align="middle"><a href="/images/news/bundle/32_select_function_features.png"><img src="/images/news/bundle/32_select_function_features.png"></a> </p>
	<p align="middle"><i>set function</i></p>
</figure>

After you calculated the transformation parameter between "bundle system" and "PART", check that the "use" attribute in the end of the tablew view is set by a checkbox. Otherwise the software will not apply this transformation to the features.

Moving back to the feature tablew view and changing to the "PART" coordinate system, you will see that the first flange circle has an x, y and z value of 0.00, because its center point is used as origin of the coordinate system. Because we expect that our tube is not exactly in level, we have should have a z value not equal to 0.00mm.

<figure>
	<p align="middle"><a href="/images/news/bundle/36_result.png"><img src="/images/news/bundle/36_result.png"></a> </p>
	<p align="middle"><i>result</i></p>
</figure>

<div style="margin: 10px">
	<a href="/files/bundle/2017 08 23 bundle guide.xml" download>Download the OpenIndy job</a>
</div>

If you have reference points for your superordinate coordinate system, check the on how to import nominal points.
[user documentaion](/documentation/docu-usr/measurement/#common-measurement-example)
