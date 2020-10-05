
<center>
<img src="img/platform/screenshot.png" alt="Screenshot" width="90%"/>
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
  [![GitHub Release Date][release_img]][release_link]
<!--
  How to deal with github stars?
  [![Stars][github_img]][github_link]
<iframe src="https://ghbtns.com/github-btn.html?user=winder&repo=Universal-G-Code-Sender&type=star&count=true" frameborder="0" scrolling="0" width="170px" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=winder&repo=Universal-G-Code-Sender&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe>
-->
</center>

-------------

## Features
* Cross platform, tested on Windows, OSX, Linux, and Raspberry Pi.
* 3D Gcode Visualizer with color coded line segments and real time tool position feedback.
* Duration estimates.
* Support for Gamepads and Joysticks
* Web pendant interface 
* Over 3000 lines of unit test code, and another 1000 lines of comments documenting the tests.
* Configuratble gcode optimization:
    * Remove comments
    * Truncate decimal precision to configurable amount
    * Convert arcs (G2/G3) to line segments
    * Remove whitespace

-------------

### GRBL 1.1 Features

1. Overrides and Toggles <br/><br/>
    Platform version only. Easily control the real time feed and speed overrides by
    enabling the Overrides widget in the Window menu.
<center>
<img src="img/platform/Overrides_window.png" alt="Overrides" width="60%"/>
</center>

2. Jog Mode <br/><br/>
    With older versions of GRBL UGS is pretty reliable when it comes to jogging, but
    there are limitations. With GRBL 1.1 this is no longer the case when using the
    new JOG MODE syntax. This first-class jog mode guarantees the GCODE state will
    be unaltered, and also allows you to stop a jog while it is in progress. UGS
    uses this new syntax automatically when it detects a version of GRBL which
    supports it. During a jog use the STOP action to stop an in-progress jog:

        >> $J=G21G91X0.7F11
        ok
        >> $J=G21G91Y0.7F11
        ok
        >> $J=G21G91Z-0.7F11
        ok

3. Pin State Reporting <br/><br/>
    Platform version only. New flags have been added to the controller state window
    to indicate when various external switches are enabled.
<center>
<img src="img/platform/Digital_readout.png" alt="Digital readout" width="40%"/>
</center>

4. Message resolution
    GRBL removed most help and error messages to make room for new features on the
    micro controller, they are now provided as data files in the grbl source code.
    UGS uses these data files to resolve all error codes and setting strings.

-------------

# Screenshots

## Platform
The next generation of UGS. Fully modular front end powered by the same robust
library created for the Classic GUI.

*Fully modular GUI, reconfigure windows to suite your needs.*
<img src="img/platform/screenshot.png" alt="Screenshot" width="90%"/>

*Built in gcode editor with line highlighter.*

<img src="img/platform/editor.png" alt="Gcode editor" width="90%"/>

*Customizable keybindings.*

<img src="img/platform/keybindings.png" alt="Key bindings" width="90%"/>

*Zoom to selection with command and drag.*

<img src="img/platform/zoom_to_region.png" alt="Zoom" width="90%"/>

*Right click in the visualizer to jog to a specific XY location.*

<img src="img/platform/click_to_jog.png" alt="Click to jog" width="90%"/>

## Classic
The classic GUI has everything you need to get started.

*3D visualizer.*

<img src="img/screenshots/visualizer.png" alt="Screenshot" width="90%"/>

*Job complete dialog.*

<img src="img/screenshots/finished.png" alt="Screenshot" width="90%"/>

*Machine control.*

<img src="img/screenshots/advanced_machine_control.png" alt="Screenshot" width="90%"/>

-------------

# Sponsors

<center>
<a href="https://www.bobscnc.com/">
<img src="img/sponsors/bobs_cnc.jpg" alt="Bob's CNC" width="40%"/>
</a>

<a href="https://jfrog.com/">
<img src="img/sponsors/artifactory.png" alt="JFrog Artifactory" width="40%"/>
</a>
<br/>

<a href="https://cloudbees.com/">
<img src="img/sponsors/cloudbees.png" alt="Cloudbees" width="40%"/>
</a>
<br/>

<a href="https://poeditor.com/">
<img src="img/sponsors/poeditor.png" alt="POEditor" width="40%"/>
</a>
</center>

-------------

# Donations

Universal Gcode Sender is free software developed and maintained in my free time for the hobby cnc community. If you would like to make a monetary donation, all proceeds will be used to try convincing my wife that it is worth my time.

<style>
  input[type="radio"] {
    margin: 0 5px 0 15px;
  }
  #donatebox {
      text-align:center;
      width: 300px;
  }
</style>

<div id="donatebox">
<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
  <!-- donation amounts -->
  <input type="radio" name="amount" value="1">$1
  <input type="radio" name="amount" value="5" checked>$5
  <input type="radio" name="amount" value="10">$10
  <br/>
  <input type="radio" name="amount" value="25">$25
  <input type="radio" name="amount" value="">Custom amount
  <br/>

  <input type="hidden" name="cmd" value="_donations">
  <input type="hidden" name="business" value="wwinder.unh@gmail.com">
  <input type="hidden" name="lc" value="US">
  <input type="hidden" name="item_name" value="Universal Gcode Sender">
  <input type="hidden" name="item_number" value="UGS Website Donate Button">
  <input type="hidden" name="no_note" value="0">
  <input type="hidden" name="currency_code" value="USD">
  <input type="hidden" name="bn" value="PP-DonationsBF:btn_donateCC_LG.gif:NonHostedGuest">
  <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" border="0" name="submit" alt="PayPal - The safer, easier way to pay online!">
  <img alt="" border="0" src="https://www.paypalobjects.com/en_US/i/scr/pixel.gif" width="1" height="1">
</form>
</div>

[java_version_img]: img/shields/Language-Java-brightgreen.svg
[java_version_link]: https://java.com/en/download/manual.jsp
[license_img]: img/shields/License-GPLv3-blue.svg
[license_link]: http://www.gnu.org/licenses/quick-guide-gplv3.en.html
[travis_img]: https://travis-ci.org/winder/Universal-G-Code-Sender.svg?branch=master
[travis_link]: https://travis-ci.org/winder/Universal-G-Code-Sender
[github_img]: https://img.shields.io/badge/Star-123-green.svg?style=social
[github_link]: https://github.com/winder/Universal-G-Code-Sender
[release_img]: https://img.shields.io/github/release/winder/Universal-G-Code-Sender
[release_link]: /download/