# UGS Platform

The UGS Platform is the next generation of Universal Gcode Sender. It is built
ontop of the Netbeans Platform which allows us to leverage its mature modular
framework. This platform allows more features to be added without compromising
on code quality, or being bogged down by a home grown framework. The Classic
GUI is used as a library, so core features benefit both interfaces.

<center>
<img src="../../img/platform/screenshot.png" alt="Screenshot" width="90%"/>
</center>

# Platform Benefits

* This is the current target for new UGS features.
* Out of the box dynamic windowing system allows arranging the UI dynamically.
* Plugin Framework available for decoupling features.
* Huge library of modules to leverage: Code Editors, Auto-updates, Keybindings

# How to run

1. Download and install the version of Java listed on the download page, [or a later version.][java_download_link]
2. [Download and extract the UGS Platform build from the downloads page.](../download.md)
3. In the locate `bin` in the `ugsplatform` directory.
4. On Windows run `ugsplatform.exe` or `ugsplatform64.exe`, on Linux or Mac OSX run `ugsplatform`.

[java_download_link]: https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0ahUKEwi05PP5z6_LAhXDvIMKHRyyB5UQFggoMAE&url=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjre8-downloads-2133155.html&usg=AFQjCNH7hWo8nDItPkEtYqoPreE_9QPZkw&cad=rja

# Usage 

## Controller state (DRO)
The Controller state (or Digital Read Out) panel displays the current status of your machine. 

<img src="../../img/guide/platform/controller_state.png" alt="Controller state (DRO)"/>

The panel provides the following functions:

* Coordinates of both the machine and your current work
* Buttons for resetting the work coordinates for each axis
* Changable work coordinates using simple mathematical expressions. <br/> You can either set an exact coordinate or, as an example, use the following `# / 2` to divide the current position in half. The `#`-character will be replaced with current position. If you start your expression with `*` or `/` the current position is prepended. <br/> <img src="../../img/guide/platform/work_coord.gif" alt="Work coordinate"/>
* Display the current machine state (Idle, Run, Jog, Alarm, etc.)
* Display the current feed rate and spindle speed
* Display the different GCode states
* Display alarm with the triggered limit switches


