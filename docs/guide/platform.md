# UGS Platform

The UGS Platform is the next generation of Universal Gcode Sender. It is built
ontop of the Netbeans Platform which allows us to leverage its mature modular
framework. This platform allows more features to be added without compromising
on code quality, or being bogged down by a home grown framework. The Classic
GUI is used as a library, so core features benefit both interfaces.

<center>
<img src="../../img/platform/screenshot.png" alt="Screenshot" width="90%"/>
</center>

## Platform Benefits

* This is the current target for new UGS features.
* Out of the box dynamic windowing system allows arranging the UI dynamically.
* Plugin Framework available for decoupling features.
* Huge library of modules to leverage: Code Editors, Auto-updates, Keybindings


# Usage 

## How to run

1. Download and install the version of Java listed on the download page, [or a later version.][java_download_link]
2. [Download and extract the UGS Platform build from the downloads page.](../download.md)
3. Go to the `ugsplatform/bin` directory.
4. On Windows run `ugsplatform.exe` or `ugsplatform64.exe`, on Linux or Mac OSX run `ugsplatform`. <br/><img src="../../img/guide/platform/run.png" alt="Run ugsplatform executable"/>

[java_download_link]: https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0ahUKEwi05PP5z6_LAhXDvIMKHRyyB5UQFggoMAE&url=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjre8-downloads-2133155.html&usg=AFQjCNH7hWo8nDItPkEtYqoPreE_9QPZkw&cad=rja


## Connecting to the controller
Start off by connecting to your controller hardware using the toolbar at the top of the program. 

1. Select the correct hardware in the firmware combo box: <br/><img src="../../img/guide/platform/connect_firmware.png" alt="Firmware combo box"/>
2. Refresh the serial ports list and select the port name for your hardware, they are usually named like the following. Make sure you have the drivers installed if you can't find the correct port in the list. <br/> - **MacOSX**: `/dev/tty.usbmodem*` or `/dev/tty.usbserial*` <br/> - **Linux**: `/dev/ttyUSB*` or `/dev/ttyACM*` <br/> - **Windows**: `COM1`, `COM2` and so on. <br/> <img src="../../img/guide/platform/connect_serial_port.png" alt="Serial port"/><br/>
3. Select the correct baud rate for your controller. <br/> - **GRBL** - version 0.9 or later are using 115200, earlier versions are using 9600. <br/> - **TinyG/g2core** will adapt to the baud rate you are connecting with so it really doesn't matter.

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


