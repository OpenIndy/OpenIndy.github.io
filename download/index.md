---
layout: page
title: Latest Version
tags: [download, OpenIndy, QT, GitHub]
comments: true
image:
  feature: banner/b_tracker2.jpg
---
<b>Version 0.6.0-14 Posted on August 23rd, 2017</b>
<br>With an open-source bundle adjustment, OpenIndy version 0.6.0-14 is now released and online on github.
Now you can combine multiple tracker stations in one bundle system, just by measuring some common points and running the bundle adjustment. You will get transformation parameters for all combinations and also you can transform all your station measurements, that are bundled, in an superordinate coordinate system of your working part (e.g. a automobile - system).

Some more details in how to use and run the bundle adjustment, you can read our blog entry about [bundle adjustment](https://openindy.github.io/news/bundle-adjustment/).
To get a good quick start, also you should check out the [user documentaion](/documentation/docu-usr/measurement/#common-measurement-example)

<br><br>
<a markdown="0" href="https://github.com/OpenIndy/OpenIndy/releases" class="btn btn-success">Download Version 0.6.0-14</a>
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
