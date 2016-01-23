
<center>
<img src="img/screenshots/sending.png" alt="Screenshot" width="90%"/>
## Universal Gcode Sender
-------------
</center>

A full featured gcode platform used for interfacing with advanced CNC controllers like [GRBL](https://github.com/grbl/grbl)
and [TinyG](https://github.com/synthetos/TinyG).
Universal Gcode Sender is a self-contained Java application which includes all external dependencies,
that means if you have the Java Runtime Environment setup UGS provides the rest.
<br/>

<center>
  <!-- Badges -->
  [![Language][java_version_img]][java_version_link]
  [![License][license_img]][license_link]
  [![Build Status][travis_img]][travis_link]
<!--
  How to deal with github stars?
  [![Stars][github_img]][github_link]
<iframe src="https://ghbtns.com/github-btn.html?user=winder&repo=Universal-G-Code-Sender&type=star&count=true" frameborder="0" scrolling="0" width="170px" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=winder&repo=Universal-G-Code-Sender&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe>
-->
</center>

-------------

## Downloads
See the [Downloads page](download.md).

-------------

## Features
* Cross platform, tested on Windows, OSX, Linux, and Raspberry Pi.
* Executable All-In-One JAR file - if you have java there is nothing to install. The JAR file includes native dependencies for all supported operating systems.
* 3D Gcode Visualizer with color coded line segments and real time tool position feedback.
* Duration estimates.
* Over 3000 lines of unit test code, and another 1000 lines of comments documenting the tests.
* Configuratble gcode optimization:
    * Remove comments
    * Truncate decimal precision to configurable amount
    * Convert arcs (G2/G3) to line segments
    * Remove whitespace

-------------

## Screenshots

<img src="img/screenshots/visualizer.png" alt="Screenshot" width="90%"/>

<img src="img/screenshots/finished.png" alt="Screenshot" width="90%"/>

<img src="img/screenshots/advanced_machine_control.png" alt="Screenshot" width="90%"/>

[java_version_img]: img/shields/Language-Java-brightgreen.svg
[java_version_link]: http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html
[license_img]: img/shields/License-GPLv3-blue.svg
[license_link]: http://www.gnu.org/licenses/quick-guide-gplv3.en.html
[travis_img]: https://travis-ci.org/winder/Universal-G-Code-Sender.svg?branch=master
[travis_link]: https://travis-ci.org/winder/Universal-G-Code-Sender
[github_img]: https://img.shields.io/badge/Star-123-green.svg?style=social
[github_link]: https://github.com/winder/Universal-G-Code-Sender
