---
layout: page
title: OpenIndy Server Interface
excerpt: "Developer documentation for OpenIndy Server Interface"
author: dev
image:
  feature: banner/b_tracker2.jpg
---


<section id="table-of-contents" class="toc">
  <header>
    <h3>Server Interface Overview</h3>
  </header>
<div id="drawer" markdown="1">
* bla
{:toc}

</div>
</section><!-- /#table-of-contents -->

---

<a href="/documentation/docu-dev.html" class="btn">Overview</a>&nbsp;&nbsp;<a href="/documentation/docu-dev/concept.html" class="btn">Concept and Architecture</a>&nbsp;&nbsp;<a href="/documentation/docu-dev/plugins.html" class="btn">Plugins</a>&nbsp;&nbsp;<a href="/documentation/docu-dev/interface.html" class="btn btn-success">Server Interface</a>&nbsp;&nbsp;<a href="/documentation/docu-dev/gui.html" class="btn">Model View Control</a>

While OpenIndy is running it is possible for a client to connect to OpenIndy via a TCP connection. A client which knows the IP and the port OpenIndy listens to, can send XML based requests to OpenIndy. OpenIndy will then perform the requested tasks and will send a XML based response message back to the client. There are various possible request types and their corresponding XML formats which are presented here.

## Request types
For a list of possible request types look at the following table.

| request type | ID | description |
| :------------- | :------------- | :----------- |
| GetProject | 0 | Get the whole OpenIndy project |
| GetActiveFeature | 1 | Get the currently selected feature |
| SetActiveFeature | 2 | Set the active feature |
| GetActiveStation | 3 | Get the active station |
| SetActiveStation | 4 | Set the active station |
| GetActiveCoordinateSystem | 5 | Get the currently selected display coordinate system |
| SetActiveCoordinateSystem | 6 | Set the display coordinate system |
| Aim | 7 | Aim the active feature with the active sensor |
| Measure | 8 | Measure the active feature with the active sensor |
| StartWatchWindow | 9 | Start a watch window stream |
| StopWatchWindow | 10 | Stop the watch window stream |
| OiToolRequest | 11 | A special OiTool request |
| GetFeatures | 12 | Get a list of all features |
| AddFeatures | 13 | Add features to OpenIndy |
| GetObservations | 14 | Get a list of observations of a geometry |
| RemoveObservations | 15 | Remove one or more observations of a geometry |
| GetParameters | 16 | Get the parameters of a feature |
| GetMeasurementConfigs | 17 | Get a list of all available measurement configs |
| GetMeasurementConfig | 18 | Get the measurement config of a geometry |
| SetMeasurementConfig | 19 | Set the measurement config of a geometry |

Each of the above request types is a somehow synchronous task. The client sends a request and OpenIndy will send a response back to the client. In addition to that, OpenIndy also sends messages to its clients asynchronously. Those messages (events) are not triggered by a client request, but are sent whenever a specific event occurs in OpenIndy. All possibile event types are listed below.

| event type | ID | description |
| :------------- | :------------- | :----------- |
| SensorActionStarted | 1001 | Informs about a started sensor action |
| SensorActionFinished | 1002 | Informs about a finished sensor action |
| MessageBox | 1003 | Sends messages that shall be displayed as a message box |
| RealTimeReading | 1004 | Get real time position information from the sensor (watch window) |
| ActiveFeatureChanged | 1005 | Informs about a new active feature |
| ActiveStationChanged | 1006 | Informs about a new active station |
| ActiveCoordinateSystemChanged | 1007 | Informs about a new active coordinate system |
| FeatureSetChanged | 1008 | Informs about added or removed features |
| FeatureAttributesChanged | 1009 | Informs about feature changes |

## Request/Response format
All request and response messages are XML based. They all have the following format:
```xml
<OiRequest id="">
</OiRequest>
```
```xml
<OiResponse ref="" errorCode="">
</OiResponse>
```
Each request comes with an id that defines the request type (see the table above). The attribute "ref" of the response tag equals the id of the corresponding request. If the "errorCode" is "0" then no error occured. The XML formats for the request and response messages to the tasks of the table above are shown below.

#### GetProject
###### Request
```xml
<OiRequest id="0"/>
```
###### Response
Look [here](https://github.com/OpenIndy/OpenIndy/wiki/OpenIndy-XML-Schema-%28openIndyXML%29) for a description of the OpenIndy XML schema.

#### GetActiveFeature
###### Request
```xml
<OiRequest id="1"/>
```
###### Response
```xml
<OiResponse ref="1" errorCode="0">
    <activeFeature ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeFeature" tag represents the id of the active feature.

#### SetActiveFeature
###### Request
```xml
<OiRequest id="2">
    <activeFeature ref=""/>
</OiRequest>
```
The attribute "ref" of the "activeFeature" tag represents the id of the feature that shall be activated.
###### Response
```xml
<OiResponse ref="2" errorCode="0">
    <activeFeature ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeFeature" tag represents the id of the active feature.

#### GetActiveStation
###### Request
```xml
<OiRequest id="3"/>
```
###### Response
```xml
<OiResponse ref="3" errorCode="0">
    <activeStation ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeStation" tag represents the id of the active station.

#### SetActiveStation
###### Request
```xml
<OiRequest id="4">
    <activeStation ref=""/>
</OiRequest>
```
The attribute "ref" of the "activeStation" tag represents the id of the station that shall be activated.
###### Response
```xml
<OiResponse ref="4" errorCode="0">
    <activeStation ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeStation" tag represents the id of the active station.

#### GetActiveCoordinateSystem
###### Request
```xml
<OiRequest id="5"/>
```
###### Response
```xml
<OiResponse ref="5" errorCode="0">
    <activeCoordinateSystem ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeCoordinateSystem" tag represents the id of the active coordinate system.

#### SetActiveCoordinateSystem
###### Request
```xml
<OiRequest id="6">
    <activeCoordinateSystem ref=""/>
</OiRequest>
```
The attribute "ref" of the "activeCoordinateSystem" tag represents the id of the coordinate system that shall be activated.
###### Response
```xml
<OiResponse ref="6" errorCode="0">
    <activeCoordinateSystem ref=""/>
</OiResponse>
```
The attribute "ref" of the "activeCoordinateSystem" tag represents the id of the active coordinate system.

#### Aim
###### Request
```xml
<OiRequest id="7">
    <feature ref=""/>
</OiRequest>
```
###### Response
```xml
<OiResponse ref="7" errorCode="0"/>
```

#### Measure
###### Request
```xml
<OiRequest id="8">
    <feature ref=""/>
</OiRequest>
```
###### Response
```xml
<OiResponse ref="8" errorCode="0"/>
```

#### StartWatchWindow
###### Request
```xml
<OiRequest id="9">
    <readingType type=""/> <!-- value between 0 and 6 -->
</OiRequest>
```
The attribute "type" of the "readingType" tag represents the type of reading (cartesian, polar etc.) that shall be returned. See the table below for a list of possible values for the attribute "type".

| reading type | description |
| :----------- | :---------- |
| 0 | Returns a distance value. |
| 1 | Returns cartesian coordinates (x, y, z). |
| 2 | Returns polar coordinates (azimuth, zenith, distance). |
| 3 | Returns azimuth and zenith. |
| 4 | Returns a temperature. |
| 5 | Returns a level measurement (RX, RY, RZ). |
| 6 | Returns cross and distance values. |
###### Response
The response message to a "StartWatchWindow" task is shown below.
```xml
<OiResponse ref="9" errorCode="0"/>
```
Until you call the "StopWatchWindow" task in regular intervals OpenIndy sends a message of the below format. Depending on the reading type that was requested one of the shown sub tags ("cartesian", "polar", etc.) will be included.
```xml
<OiResponse ref="9" errorCode="0">
    <geometry id="" name="" />
    <cartesian x="" y="" z=""/>
    <polar azimuth="" zenith="" d=""/>
    <distance d=""/>
    <direction r=""/>
    <temperature t=""/>
    <level RX="" RY="" RZ=""/>
</OiResponse>
```

#### StopWatchWindow
###### Request
```xml
<OiRequest id="10"/>
```
###### Response
```xml
<OiResponse ref="10" errorCode="0"/>
```

#### OiToolRequest
###### Request
```xml
<OiRequest id="11">
    <tool iid="" />
    <!-- dynamic content which depends on the OiTool-plugin -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="11" errorCode="0">
    <tool iid="" />
    <!-- dynamic content which depends on the OiTool-plugin -->
</OiResponse>
```

#### GetFeatures
###### Request
```xml
<OiRequest id="12"/>
```
###### Response
```xml
<OiResponse ref="12" errorCode="0">
    <feature> <!-- can contain 0 to n features -->
        <feature type=""> <!-- type: see table below for available feature types -->
             <id></id>
             <name></name>
             <group></group>
             <isSolved></isSolved>
             <isNominal></isNominal> <!-- only included for geometries -->
        </feature>
    </feature>
</OiResponse>
```
| type | feature |
| :----------- | :---------- |
| 0 | circle |
| 1 | cone |
| 2 | cylinder |
| 3 | ellipse |
| 4 | ellipsoid |
| 5 | hyperboloid |
| 6 | line |
| 7 | nurbs |
| 8 | paraboloid |
| 9 | plane |
| 10 | point |
| 11 | point cloud |
| 12 | angle (scalar entity) |
| 13 | distance (scalar entity) |
| 14 | measurement series (scalar entity) |
| 15 | temperature (scalar entity) |
| 16 | slotted hole |
| 17 | sphere |
| 18 | torus |
| 19 | coordinate system |
| 20 | station |
| 21 | transformation parameter |

#### AddFeatures
###### Request
```xml
<OiRequest id="13">
    <type></type>
    <name></name>
    <group></group>
    <count></count>
    <isActual></isActual> <!-- only for geometries (0=false, 1=true) -->
    <isNominal></isNominal> <!-- only for geometries (0=false, 1=true) -->
    <nominalSystem></nominalSystem> <!-- only for geometries -->
    <measurementConfig></measurementConfig> <!-- only for geometries -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="13" errorCode="0"/>
```

#### GetObservations
###### Request
```xml
<OiRequest id="14">
    <id></id> <!-- id of the geometry whose observations shall be delivered -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="14" errorCode="0">
    <id></id> <!-- geometry id -->
    <observations> <!-- can contain 0 to n observations -->
        <observation>
            <id></id>
            <x></x>
            <y></x>
            <z></x>
            <vx></vx>
            <vy></vx>
            <vz></vx>
            <v></v>
            <isUsed></isUsed>
            <isValid></isValid>
        </observation>
    </observations>
</OiResponse>
```

#### RemoveObservations
###### Request
```xml
<OiRequest id="15">
    <id></id> <!-- geometry id -->
    <observations> <!-- can contain 0 to n observations -->
        <observation id=""/>
    </observations>
</OiRequest>
```
###### Response
```xml
<OiResponse ref="15" errorCode="0"/>
```

#### GetParameters
###### Request
```xml
<OiRequest id="16">
    <id></id> <!-- id of the feature whose parameters shall be delivered -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="16" errorCode="0">
    <id></id> <!-- feature id -->
    <stdev></stdev>
    <parameters>
        <parameter name="" value=""/>
    </parameters>
</OiResponse>
```
Possible parameters are: "x", "y", "z", "i", "j", "k", "i 2", "j 2", "k 2", "i 3", "j 3", "k 3", "radius", "radius 2", "aperture", "a", "b", "c", "angle", "distance", "measurement series", "temperature", "length", "tx", "ty", "tz", "rx", "ry", "rz", "sx", "sy", "sz"

#### GetMeasurementConfigs
###### Request
```xml
<OiRequest id="17"/>
```
###### Response
```xml
<OiResponse ref="17" errorCode="0">
    <measurementConfigs>
        <measurementConfig>
            <name></name>
            <isSaved></isSaved>
            <count></count>
            <iterations></iterations>
            <measureTwoSides></measureTwoSides>
            <timeDependent></timeDependent>
            <distanceDependent></distanceDependent>
            <timeInterval></timeInterval>
            <distanceInterval></distanceInterval>
            <typeOfReading></typeOfReading>
        </measurementConfig>
    </measurementConfigs>
</OiResponse>
```

#### GetMeasurementConfig
###### Request
```xml
<OiRequest id="18">
    <id></id> <!-- id of the geometry whose measurement config shall be delivered -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="18" errorCode="0">
    <id></id> <!-- geometry id -->
    <measurementConfig>
        <name></name>
        <isSaved></isSaved>
        <count></count>
        <iterations></iterations>
        <measureTwoSides></measureTwoSides>
        <timeDependent></timeDependent>
        <distanceDependent></distanceDependent>
        <timeInterval></timeInterval>
        <distanceInterval></distanceInterval>
        <typeOfReading></typeOfReading>
    </measurementConfig>
</OiResponse>
```

#### SetMeasurementConfig
###### Request
```xml
<OiRequest id="19">
    <id></id> <!-- geometry id -->
    <measurementConfig></measurementConfig> <!-- name of the measurement config -->
    <isSaved></isSaved> <!-- 0=project config, 1=saved config -->
</OiRequest>
```
###### Response
```xml
<OiResponse ref="19" errorCode="0"/>
```

## Event format
All event messages are XML based. They all have the following format:
```xml
<OiResponse ref="" errorCode="">
</OiResponse>
```
Each event comes with an id that defines the event type (see the table above). If the "errorCode" is "0" then no error occured. The XML formats for the events are shown below.

#### SensorActionStarted
```xml
<OiResponse ref="1001" errorCode="0">
    <action name=""/>
</OiResponse>
```

#### SensorActionFinished
```xml
<OiResponse ref="1002" errorCode="0">
    <action success="1" message=""/> <!-- success: 1=true, 0=false -->
</OiResponse>
```

#### MessageBox
```xml
<OiResponse ref="1003" errorCode="0">
    <message text="" type="0"/> <!-- type: 0=information, 1=warning, 2=error, 3=critical -->
</OiResponse>
```

#### RealTimeReading
```xml
<OiResponse ref="1004" errorCode="0">
    <measurement name="" value=""/> <!-- name=x|y|z|azimuth|zenith|distance -->
</OiResponse>
```

#### ActiveFeatureChanged
```xml
<OiResponse ref="1005" errorCode="0"/>
```

#### ActiveStationChanged
```xml
<OiResponse ref="1006" errorCode="0"/>
```

#### ActiveCoordinateSystemChanged
```xml
<OiResponse ref="1007" errorCode="0"/>
```

#### FeatureSetChanged
```xml
<OiResponse ref="1008" errorCode="0"/>
```

#### FeatureAttributesChanged
```xml
<OiResponse ref="1009" errorCode="0"/>
```

## Error codes
| error code | description |
| :------------- | :----------- |
| 0 | No error occured. |
| 1 | No OpenIndy job available. |
| 2 | No, or wrong, xml format. |
| 3 | The request id does not exist. |
| 4 | There is no active feature. (e.g. measure) |
| 5 | There is no active station. |
| 6 | There is no active coordinate system. |
| 7 | The requested feature id does not exist. |
| 8 | No transformation parameters are available. (e.g. aim) |
| 9 | The task is already in process. (e.g. watch window) |
| 10 | There is no task that could be stopped. (e.g. watch window) |
| 11 | No sensor is available. (e.g. watch window) |
| 12 | The task id does not exist. |
| 13 | You cannot measure a nominal geometry. |
| 13 | Measurement error. |
| 13 | No sensor is connected. |
| 13 | The feature is not solved. |
