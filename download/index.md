---
layout: page
title: Latest Version
tags: [download, OpenIndy, QT, GitHub]
comments: true
image:
  feature: banner/b_tracker2.jpg
---
<b>Version 0.8.0-16 Posted on November 14th, 2017</b>
<br>The big focus of this update was to improve the workflow of setting, changing and removing functions. The dialog is now accessible by right clicking the feature or double clicking the function column. This also had some effect on the column order of transformation parameters.
Also now all observations have a better representation in the dialog.

[Modul] The RoboCalc algorithm was improved, because of the definition of ABB quaternions and all functionality got some improved stability.
In the settings you can choose to play sounds for measurement now.

To get a good quick start, also you should check out the [user documentaion](/documentation/docu-usr/measurement/#common-measurement-example)

<br><br>
<a markdown="0" href="https://github.com/OpenIndy/OpenIndy/releases" class="btn btn-success">Download Version 0.8.0-16</a>
<h1>Sourcecode</h1>
To join our community and support us in the ongoing development, you can also fork the repository of the project on [GitHub](https://github.com/OpenIndy/OpenIndy).
<br><br>
<a markdown="0" href="https://github.com/OpenIndy/OpenIndy" class="btn btn-info">Fork the Repository on GitHub</a>
<h1>Other Downloads</h1>
The development framework of your choice should be QT Creator which is designed to streamline the creation of applications and user interfaces to target multiple platforms with one code base.
<br><br>
<a markdown="0" href="http://qt-project.org/downloads" class="btn btn-info">Download Qt Creator</a>
<br><br>

Build Guide
====

----

IDE
----
As mentioned above, OpenIndy is developed with the [Qt framework](http://qt-project.org/downloads) (Qt libs + Qt Creator IDE).
To configure Qt Creator you may follow the instructions at the [Qt documentation](http://qt-project.org/doc/qtcreator-3.0/creator-configuring.html).

Dependencies
------------

- [OpenIndy-Math](https://github.com/OpenIndy/OpenIndy-Math)
- [OpenIndy-Core](https://github.com/OpenIndy/OpenIndy-Core)
- [amadillo c++ linear algebra library](http://arma.sourceforge.net)
- [BLAS/LAPACK](http://www.netlib.org/lapack/)
- [Qt](http://qt-project.org)
- [sqlite](https://sqlite.org)
