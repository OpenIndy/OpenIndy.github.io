---
layout: page
title: Preperation
excerpt: "User documentation for OpenIndy - Preperation"
author: usr
image:
  feature: banner/b_smr.jpg
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Preperation Overview</h3>
  </header>
<div id="drawer" markdown="1">
* bla
{:toc}

</div>
</section><!-- /#table-of-contents -->

---

<a href="/documentation/docu-usr" class="btn">Overview</a>&nbsp;&nbsp;<a href="/documentation/docu-usr/preperation" class="btn">Preperation</a>&nbsp;&nbsp;<a href="/documentation/docu-usr/measurement" class="btn">Measurement</a>&nbsp;&nbsp;

<br>

### Load plugins in OpenIndy

The current download version of [OpenIndy](/download) includes the pre-installed [OpenIndy-DefaultPlugin](https://github.com/OpenIndy/OpenIndy-DefaultPlugin), which includes a bunch of functionalities.<br><br>
To load another plugin click on the menu **Plugin > load plugins**. After this a new window opens, where you have to select the location of your plugin. After accepting the folder dialog, OpenIndy shows you the metadata of the selected plugin and checks if it is valid. Press Ok and then ok in the window to load it. OpenIndy will then automatically copy the plugin and all its dependencies to the plugin directory, so that you can work with it.
The next time you start OpenIndy, the plugins will be loaded automatically.
<figure >
	<a href="../images/usr/cme/loadPlugin.png"><img src="/documentation/images/usr/cme/loadPlugin.png"></a>
	<p align="middle"><i>The "load plugin" dialog</i></p>
</figure>
