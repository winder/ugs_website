# Common Problems

## "Grbl has not finished booting."

This happens when UGS connects to a serial port and does not receive the GRBL startup string. Typically this is caused by a configuration problem and can be solved by one of the following:

1. Check the baud rate is 115200, or 9600 for very old versions of grbl.
2. Make sure you are connecting to the correct port.
3. Make sure you have installed any drivers required for your controller.
4. Make sure GRBL is properly flashed on your controller.
5. As a last resort try removing all previous UGS settings (see <a href="#property-files">property Files</a>) and reinstall.

## Gcode program stopped working

The UGS Parser has a configurable list of rules to skip certain patterns, these rules are typically added by a Yes/No dialog asking if you would like to skip the erroneous commands in the future. Sometimes GRBL will get into an ALARM state and there will be lots of these popups which should not be skipped in the future.

<center>
<img src="../../img/common/bad.code.dialog.png" alt="Screenshot" width="90%"/>
</center>

Skipping good commands may lead to broken gcode. Those rules should be removed from the gcode processor by going into the controller options.

In UGS Classic the option is in <b>Settings > Gcode Processor Configuration</b>.

In UGS Platform the option is under <b>Preferences... > UGS > Controller Options</b>.

For both, you need to uncheck or remove the invalid settings in the bottom list:

<center>
<img src="../../img/common/bad.code.setting.png" alt="Screenshot" width="90%"/>
</center>

# Platform Specific Issues

## Toolbars or Windows don't appear.

This usually happens if you try running the platform without the required version of Java. The user cache is initialized but some objects become corrupt and initialization fails in the future even after upgrading Java.

This can be fixed by clearing out the user cache directory which can be found on the UGS "About" screen seen in the image below.
<br/>
<center>
<img src="../../img/platform/about_popup.png" alt="Screenshot" width="60%"/>
</center>

# Information

## Property Files

Occasionally it is useful to attach some of these property files to bug reports to help with reproducing a problem.

### Classic

Classic UGS properties are stored in your home directory, which changes based on the operating system being used:

* **Windows**: /home/user/ugs
* **Mac**: ~/Library/Preferences/ugs
* **Linux**: ~/ugs

Files include <b>UniversalGcodeSender.json</b> which contain different settings, and a <b>firmware_config</b> directory which contains several configurations for different firmwares and testing profiles.

### Platform

Platform UGS properties are stored in your home directory:

* **Windows**: /home/user/ugs
* **Mac**: ~/Library/Preferences/ugs
* **Linux**: ~/ugs

The platform version of UGS contains additional property files automatically created by the NetBeans Platform.
These files are also contained in various locations based on the operating system being used. You can find the exact locations of these files in the About / Help menu.
It is sometimes necessary to clear out these properties between major feature updates.
<br/>
<center>
<img src="../../img/platform/about_popup.png" alt="Screenshot" width="60%"/>
</center>

Logs are typically located in these directories:

* **Windows 7**: C:\Users\username\AppData\Roaming\ugsplatform\2.0-SNAPSHOT\var\log\messages.log
* **Windows XP**: C:\Documents and Settings\username\Application Data\ugsplatform\2.0-SNAPSHOT\var\log\messages.log
* **Mac**: ~/Library/Application Support/ugsplatform\2.0-SNAPSHOT/var/log/messages.log
* **Linux**: ~/.ugsplatform/2.0-SNAPSHOT/var/log/messages.log


# Operating System Compatibility Problems

## Linux: Non Reparenting Window Managers

There are a number of window managers which are "[non reparenting](https://en.wikipedia.org/wiki/Re-parenting_window_manager)", this causes some problems with Java.

Some details about this problem [can be seen here](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/258374).

Use the **_JAVA_AWT_WM_NONREPARENTING** environment property to fix the problem:
```shell
export _JAVA_AWT_WM_NONREPARENTING=1
```

# Program Slows Down and Send Freezes

If you notice slowness while running your program, it may mean UGS is running out of available memory. There are a couple things to try:

1. Check the controller settings, and make sure "Arc Expander" is not enabled. This can take a small program and turn it into a very large one by converting arcs into many small movements.
2. Increase the memory allocated to UGS by navigating the the intsallation directory (See paths above). There is a folder named `etc` containing `ugsplatform.conf`, open this file with a simple text editor and modify the value of Xms to something like `-J-Xms256m`, or larger. [Additional details can be found here](http://wiki.netbeans.org/FaqSettingHeapSize).

