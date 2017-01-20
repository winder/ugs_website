# Common Features

Because the UGS Platform and the Classic GUI both build on the same foundation
they have a lot in common.

# Gcode Processing

## Error handling

When GRBL reports an error while processing a line of gcode UGS will
automatically pause the stream. In some cases you might want to continue and
ignore the error in the future. The following dialog is displayed allowing you
to do so:

<center>
<img src="../../img/common/bad.code.dialog.png" alt="Screenshot" width="90%"/>
</center>

If you select 'yes' at this point, a line will be added to the controller
options:

<center>
<img src="../../img/common/bad.code.setting.png" alt="Screenshot" width="90%"/>
</center>

