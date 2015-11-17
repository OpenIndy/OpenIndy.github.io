---
layout: page
title: Measurement
excerpt: "User documentation for OpenIndy - The Measurement"
author: usr
image:
  feature: banner/b_smr.jpg
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Measurement Overview</h3>
  </header>
<div id="drawer" markdown="1">
* bla
{:toc}

</div>
</section><!-- /#table-of-contents -->

---

<a href="/documentation/docu-usr.html" class="btn">Overview</a>&nbsp;&nbsp;<a href="/documentation/docu-usr/preperation.html" class="btn">Preperation</a>&nbsp;&nbsp;<a href="/documentation/docu-usr/measurement.html" class="btn">Measurement</a>&nbsp;&nbsp;


##Simulation (virtual Laser-Tracker)

This section shows a simple measurement task with the implemented virtual Laser-Tracker.
The task is to measure a point and a plane and register the point into the plane.

<figure >
	<p align="middle"><a href="../images/usr/vlt/error_model.PNG"><img src="/documentation/images/usr/vlt/error_model.PNG"></a> </p>
	<p align="middle"><i>error model of the virtual Laser-Tracker (16 errors)</i></p>
</figure>

###Connect/Start the virtual Laser-Tracker

The first step is to set and connect the virtual sensor. The instrument is set at the active station. On default, STATION01 is the active station and is marked in dark grey.
Other stations, if you have some, are marked light grey. Only one station can be active, but it is possible to switch them. <br>
To set the instrument click **Station > set sensor**.
The following dialog will appear:

<figure >
	<p align="middle"><a href="../images/usr/vlt/set_virtualLaserTracker.PNG"><img src="/documentation/images/usr/vlt/set_virtualLaserTracker.PNG"></a> </p>
	<p align="middle"><i>set instrument dialog</i></p>
</figure>

In this dialog you first have to select your sensor type, which is laser tracker in the screenshot. After that you choose the **VirtualTracker** by selecting it in the list view and pressing set. The programm now asks you if you want to connect the sensor automatically, confirm with yes.

###Configure the measurement task

We will working in the **Station-Coordinatesystem** (original coordinate system of the selected sensor). For that use the combobox on the left side, right above the table-view. Switch from PART to STATION01.

In the next step you need to create the features you want to measure. For this use the toolbar on the left. There is a button for each feature you can create. Clicking on one of them opens the creation dialog, where you can put in
your settings and parameters for the features you want to create.

For the task you need to create a point and a plane. Click on **Create point** ![create point](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/feature/Point.png){: style="width: 25px"}, type in the name "p1". They are not common and not nominal. Leave the default function as BestFitPoint.  After clicking on create, the point will be created. Repeat the same procedure for creating a plane > **Create plane** ![create point](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/feature/Plane.png){: style="width: 25px"}

###Add register Function to the point-feature

For our task we need a function, which will register our point into the plane. To do this, select the point and click **Function > set function** or use the ![set function](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/standard/function.png){: style="width: 20px"}. Select the new **new function** tab and double click on **Register**. In the list view you have to choose the **Regsiter-Function** and set up all necessary parameters (here you choose the created plane).

<figure >
	<p align="middle"><a href="../images/usr/vlt/configuration_of_measurement.png"><img src="/documentation/images/usr/vlt/configuration_of_measurement.png"></a> </p>
	<p align="middle"><i>configuration of measurement</i></p>
</figure>

###Measurement

After the features are created, functions are applied and the sensor is set and connected, we can start measuring the features. For this, select the feature you want
to measure and click on **measure** in the sensor control pad. You can find it by clicking **View > sensor control** or by clicking on the ![sensor control pad](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/standard/sensor%20control%20pad.png){: style="width: 25px"} Before you can measure you have to choose at which **actual position** the virtual sensor is pointing at.
Click on the **move** command in the sensor control pad and choose a 3D-Position. <br>

**Point**
- 0/0/10

**Plane**
- 12/12/0
- 12/14/0
- 14/14/0
- 14/12/0

<figure >
 <p align="middle"><a href="../images/usr/vlt/move_cmd.png"><img src="/documentation/images/usr/vlt/move_cmd.png"></a> </p>
 <p align="middle"><i>move command</i></p>
</figure>

###Result

After all mesurements are finished, the table view shows the result set. For the "registered" point you get the 3D-position
(x= 0, y=0 , z=10.0->0.0). For the plane you get a 3D-position (x/y/z) and a 3D-direction (i/j/k). For all measured geometries you get information about the accuracy (stdev).

<figure >
 <p align="middle"><a href="../images/usr/vlt/result.png"><img src="/documentation/images/usr/vlt/result.png"></a> </p>
 <p align="middle"><i>result set</i></p>
</figure>


##Common measurement example

This section shows one possible way to solve an example task. There are also other ways or orders of steps to solve it.

###The measurement task
The task is to check some features of the object vs CAD nominal data. Ten focal points of drill-holes have to be checked against a nominal CAD data. The coordinates of the nominal data are in the object coordinate system, so you also have to transform between the instrument
coordinatesystem and the object coordinatesystem. The four marked drill-holes are used as checkpoints for the transformation.
<figure >
	<img src="/documentation/images/usr/cme/object.jpg"></a>
	<p align="middle"><i>the object that has to be checked</i></p>
</figure>

###Set instrument
The first step is to set and connect an instrument. The instrument is set at the active station. On default, STATION01 is the active station and is marked in dark grey.
Other stations, if you have some, are marked light grey. Only one station can be active, but it is possible to switch them. <br>
To set the instrument click **Station > set sensor**.
The following dialog will appear:
<figure >
	<p align="middle"><a href="../images/usr/cme/setInstrument.png"><img src="/documentation/images/usr/setInstrument.png"></a> </p>
	<p align="middle"><i>set instrument dialog</i></p>
</figure>
In this dialog you first have to select your sensor type, which is laser tracker in the screenshot. After that you choose the instrument by selecting it in the list view and pressing set. The programm now asks you if you want to connect the sensor automatically, or if you want to connect to it later by hand.

###Import nominal data
One of the first steps to solve the task is to import the nominal data (are tagged as golden rows) for the drill-holes. To do this. click on **File > import > nominals**.
In the import dialog choose the data format which is ASCII in our example and the geometry typ (point). As third parameter you need to choose the destination coordinatesystem for the nominal geometries. In our case use the default PART coordinate system, which is the coordinate system of the not yet transformed plain.
You can also choose other coordinate systems, if you create them via the toolbar by clicking on ![create coordinate system](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/feature/Coordinatesystem.png){: style="width: 25px"} before importing the nominal data.
<br><br>
<i>The nominal points file for the measurement task:</i><br>
p1 -50.737 0.082 0.000<br>
p2 -35.867 36.062 0.000<br>
p3 0.096 50.816 0.000<br>
p4 35.924 35.920 0.000<br>
p5 50.796 0.012 0.000<br>
p6 35.861 -35.981 0.000<br>
p7 -0.086 -50.734 0.000<br>
p8 -36.015 -35.797 0.000<br>
p9 0.000 0.000 0.000<br>
p10 104.199 0.000 0.000

<figure >
	<a href="../images/usr/cme/importNominals.png"><img src="/documentation/images/usr/cme/importNominals.png"></a>
	<p align="middle"><i>import nominal dialog</i></p>
</figure>

###Create features to be measured
In the next step you need to create the features you want to measure. For this use the toolbar on the left. There is a button for each feature you can create. Clicking on one of them opens the creation dialog, where you can put in
your settings and parameters for the features you want to create.

For the task you need to create 10 points. The name of the actual measurement features has to be the same as the corresponding nominal one. Click on **Create point** ![create point](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/feature/Point.png){: style="width: 25px"}, type in the name "p1" and set the count = 10. They are not common and not nominal. Leave the default function as BestFitPoint.  After clicking on create, ten points will be created and automatically be named after the count number from p1 to p10.
<figure >
	<p align="middle"><a href="../images/usr/cme/createFeatureDialog.png"><img src="/documentation/images/usr/cme/createFeatureDialog.png"></a> </p>
	<p align="middle"><i>create feature dialog</i></p>
</figure>
<br>

###Add functions
To solve a feature it is neccessary to add functions to it. You already set the default function in the create feature dialog. Every function has input parameters, that you have to assign to it (e.g. obervations or a plane and a
distance). For our task we added a "Best Fit function" to the features we measure in the creation dialog. To do this manually, select a feature and click **Function > set function** or use the ![set function](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/standard/function.png){: style="width: 20px"}
icon. Then choose your function by clicking it. There are only functions displayed, that can be applied to the selected feature at this state.
After double clicking the next view appears, where you can add or remove the input parameters that the function needs. Also you see all functions that are
applied to this feature in the order they are performed.
In our case we first add the best fit function and then measure the feature, so all observations of the feature are used for the best fit immediately.
It is also possible to measure the feature first and then add the function. This way you have to assign the observations of the feature to the function via
the treeviews in the function menu.
<figure >
	<a href="../images/usr/cme/assignInputParameter.png"><img src="/documentation/images/usr/cme/assignInputParameter.png"></a>
	<p align="middle"><i>add input parameter.</i></p>
</figure>

You can remove functions by doing a right click on them in the function menu and choosing **delete function**.

###Measuring features
After the features are created, functions are applied and the sensor is set and connected, we can start measuring the features. For this, select the feature you want
to measure and click on **measure** in the sensor control pad. You can find it by clicking **View > sensor control** or by clicking on the ![sensor control pad](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/standard/sensor%20control%20pad.png){: style="width: 25px"} icon.

<figure >
	<a href="../images/usr/cme/measure.png"><img src="/documentation/images/usr/cme/measure.png"></a>
	<p align="middle"><i>measure the current selected feature (p1)</i></p>
</figure>

You will notice, that the measured points are displayed as not yet solved (columns are tagged yellow). Because we could not measure the focal point of the drillholes directly, we need to solve the problem by applying some functions.
<figure >
	<p align="middle"><img src="/documentation/images/usr/cme/offSetProblem.JPG"></a> </p>
	<p align="middle"><i>unknown offset problem</i></p>
</figure>

For this, we measure the ground plane, and move it on its own normal vector with the value of the reflector radius. To do this use the function
"Shift".
After this we project our drill-hole points in the plane and have the offset corrected values we want.

###Transformation parameter
After measuring all neccessary features, we need to transform our measurements, because the nominal data for the feature is in the PART system whereas
the actual feature data is in the instrument coordinate system. In order to do this, we need to create a transformation parameter via the button
**Create transformation parameter** ![create transformation parameter](https://raw.githubusercontent.com/OpenIndy/OpenIndy/master/res/icons/toolbars/feature/TrafoParam.png){: style="width: 25px"}. In the dialog you have to give this transformation parameter a name and set a start and destination coordinate system. After creating
the parameter set it is displayed in its own tableview tab "transformation parameter". Here you can select it by clicking on it. You can also edit the parameters
by hand if you choose "show properties" after right clicking the transformation parameter set.

####Apply a function to the transformation parameter
{:.no_toc}
After you created the transformation parameter you can set some values by hand (see paragraph above), or you can calculate parameters by applying a function
to the transformation parameter feature. Click on **Function > set function** and click on the tab "new function". The default plugin, that we used for this measurement task, contains a 7 parameter helmert transformation. Select the transformation function by double clicking it.

####Apply checkpoints to the 7 parameter transformation
{:.no_toc}
After selecting the function, the input parameter have to be applied to the function. In the available elements window, we need to apply the nominal (imported at the beginning)
and actual (measured) checkpoints, specified at the beginning of the guide (p1,p3,p5,p7). Apply the dialog and now the transformation parameter will be calculated and applied on the feature.

<figure >
	<a href="../images/usr/cme/7parameterTransformation.png"><img src="/documentation/images/usr/cme/7parameterTransformation.png"></a>
	<p align="middle"><i>applying checkpoints (nominal and actual) to the function</i></p>
</figure>

After this step it is important to change the "use" column of the transformation parameter feature from false to true by double clicking the matching field, so that the parameter can be applied as transformation on the coordinate systems.<br>
Now it is possible to transform between STATION01 and PART. You can do this, by switching the active coordinate system in the combobox right above the feature tableview. This combobox includes all existing coordinate systems whether instrument systems or part systems.


###Save and load project
After the actual values are transformed and compared with the nominal values of the features, you should save the project by clicking on **File > save as** and specify a path and folder.
OpenIndy saves the project in an openindyXML.xml file where all features, their relations, observations, functions and other parameters are stored, so that it is possible to
restore the complete project at a later time. To load and restore a project click **File > open project**.
<figure >
	<a href="../images/usr/cme/exampleProjectFile.png"><img src="/documentation/images/usr/cme/exampleProjectFile.png"></a>
	<p align="middle"><i>extract of a project xml file</i></p>
</figure>
