# Backend architecture

Similar to the front-end there are more layers on the backend to help with
supporting differences between different gcode controllers and the different
ways to communicate with these controllers. Because UGS depends on serial
events from CNC devices, the communication between layers is also event driven.
This is implemented using a series of **Listener** classes which pass messages
from the lower levels to the upper levels whenever data is detected on the
serial port (USB).

## Controller

A controller is primarily responsible for implementing controller-specific
features. Different features can be things like what happens when a
`Perform Homing` command is requested, or how to issue status requests and
parse their results. `GRBL` and `TinyG` are both supported, they share a
lot of code with the **AbstractController.java** abstract class.

Internally the **AbstractController** class implements several important
things. It manages the stream lifecycle, keeping track of which commands have
been sent, which have been completed and in some cases which are queued for
sending. The controller also figures out when the stream has finished. Finally
the **AbstractController** implements the `SerialCommunicatorListener`, which
how its able to detect all of this state information (and allows commands to
be sent to the CNC controller).

The controller provides a `ControllerListener` interface which is used to
provide real time status.

Finally, the **AbstractController** defines a number of abstract methods which
can be used by device specific controllers as needed to hook into important
lifecycle events:
```java
    abstract protected void closeCommBeforeEvent();
    abstract protected void closeCommAfterEvent();
    protected void openCommAfterEvent() throws Exception {}
    abstract protected void cancelSendBeforeEvent();
    abstract protected void cancelSendAfterEvent();
    abstract protected void pauseStreamingEvent() throws Exception;
    abstract protected void resumeStreamingEvent() throws Exception;
    abstract protected void isReadyToSendCommandsEvent() throws Exception;
    abstract protected void statusUpdatesEnabledValueChanged(boolean enabled);
    abstract protected void statusUpdatesRateValueChanged(int rate);

    // This one is special, because it is responsible for parsing device
    // responses, such as a command complete, status string, or parsing a
    // status event. In the case of a command complete, it must call
    // `commandComplete` to push the stream lifecycle along.
    abstract protected void rawResponseHandler(String response);
```

Here is the public interface which controlles conform to:
```java
public interface IController {
    /*
    Observable
    */
    public void addListener(ControllerListener cl);

    /*
    Actions
    */
    public void performHomingCycle() throws Exception;
    public void returnToHome() throws Exception;
    public void resetCoordinatesToZero() throws Exception;
    public void resetCoordinateToZero(final char coord) throws Exception;
    public void killAlarmLock() throws Exception;
    public void toggleCheckMode() throws Exception;
    public void viewParserState() throws Exception;
    public void issueSoftReset() throws Exception;

    /*
    Behavior
    */
    public void setSingleStepMode(boolean enabled);
    public boolean getSingleStepMode();

    public void setStatusUpdatesEnabled(boolean enabled);
    public boolean getStatusUpdatesEnabled();
    
    public void setStatusUpdateRate(int rate);
    public int getStatusUpdateRate();
    
    public GcodeCommandCreator getCommandCreator();
    public long getJobLengthEstimate(File gcodeFile);
    
    /*
    Serial
    */
    public Boolean openCommPort(String port, int portRate) throws Exception;
    public Boolean closeCommPort() throws Exception;
    public Boolean isCommOpen();
    
    /*
    Stream information
    */
    public Boolean isReadyToStreamFile() throws Exception;
    public Boolean isStreamingFile();
    public long getSendDuration();
    public int rowsInSend();
    public int rowsSent();
    public int rowsRemaining();
    
    /*
    Stream control
    */
    public void beginStreaming() throws Exception;
    public void pauseStreaming() throws Exception;
    public void resumeStreaming() throws Exception;
    public void cancelSend();

    /*
    Stream content
    */
    public GcodeCommand createCommand(String gcode) throws Exception;
    public void sendCommandImmediately(GcodeCommand cmd) throws Exception;
    public void queueCommand(GcodeCommand cmd) throws Exception;
    public void queueStream(GcodeStreamReader r);
    public void queueRawStream(Reader r);
}
```


## Communicator

A communicator handles all levels of sending data to the device. Raw responses
are returned to any listeners via the `SerialCommunicatorListener`.

The `AbstractCommunicator` implements several listener utilities which are used
by implementing classes.

The `BufferedCommunicator` abstract class handles the process of buffering
multiple commands at once in order to keep a constant stream of commands
available to the CNC device. It does this in the **streamCommands** method by
maintaining a list of active commands, and the current size of those commands. A
method named `processedCommand` must be implemented in a subclass to determine
whether a raw response indicates a command has completed. This notifies the
**BufferedCommunicator** that it should attempt to send more commands.

`GrblCommunicator` and `TinyGCommunicator` are two concrete implementations of
the **BufferedCommunicator**.

## Connection

This is a very thin layer which provides a way to write and receive data:
```java
    abstract public boolean openPort(String name, int baud) throws Exception;
    abstract public void closePort() throws Exception;
    abstract public boolean isOpen();
    abstract public void sendByteImmediately(byte b) throws Exception;
    abstract public void sendStringToComm(String command) throws Exception;
```

# Streaming strategy

UGS attempts to use a fixed amount of memory when streaming a file. In this way
it can send gcode files of any size. Files are preprocessed at the `BackendAPI`
level using the `GcodeStreamWriter` class. This will serialize all the required
metadata into a file. Later on that file can be opened with the
`GcodeStreamReader` class, the **Controller** and **Communicator** classes use
this. Using the reader, the **Communicator** class can pull out commands one at
a time and send them to the **Connection**.
