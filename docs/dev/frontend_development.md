# Front-end Architecture

UGS uses a Model-View-Presenter architecture. What this means is that at a high
level there are three layers which each serve different purposes. A **Model**
for all backend logic, a **View** displayed to the user and a **Presenter**
which serves as a buffer between the model and one or more views.

# Model

The model contains all backend logic. Things like opening a connection, listing
serial ports, streaming a file, and handling firmware specific nuances. All of
this is hidden from the front end as much as possible.

# View

The view only has access to the presenter. It is responsible for all user
interaction and feedback. The main logic in here should be things like
enabling or disabling components based on the current state of the model.

## Classic GUI

The **Classic GUI** is built using NetBeans. There are a number of custom Swing
components, and they are all initialized with the NetBeans GUI builder. The
vast majority of the **Classic GUI** code is contained in `MainWindow.java`.
There isn't a lot to expand on here, this front end has grown organically over
the years and is fairly rigid. The `Visualizer` component is a standalone
JOGL window which is updated using events from the backend (it was a model for
many of the improvements in the current applications architecture).

## UGS Platform

The **UGS Platform** build is also built using NetBeans. It is a built ontop of
the NetBeans Platform which provides it a robust set of tools like flexible
windows, a plugin framework, and a suite of tools for module communications. At
the core of this is a module named `UGSLib` which is a simple wrapper to the
standard UGS JAR file. There is a suite of modules named `UGSCore` which
provides many of the standard UI elements seen in the **Classic GUI**, in
addition there are other modules that provide new functionality.

Extending the GUI is now a matter of creating a new plugin, for details on how
to do this see the [Plugin Tutorial](plugin.md).

# Presenter

The presenter serves as an API for the model. All the heavy lifting needed for
the GUI should happen here. For example the controller model object knows how
to stream a processed file, but it doesn't know how to process the file. So the
presenter will pass data to the gcode processor and generate a processed object
which can be passed to the controller.

Similarly, all notifications from the model are reinterpreted for the view with
a simpler message strategy.

In this way, all updates to the backend code can be leveraged by all front ends
which utilize UGS.

## BackendAPI

In UGS interfaces named `BackendAPI` and `BackendAPIReadOnly` provide the
presenter layer. The read only methods are split off into a sub-interface in
case a developer wants to be sure they don't change any state. For instance a
widget that displays the current machine location probably has no need for
pausing a stream.

These APIs are used by all front ends (**Classic GUI**, **PendantUI** and
**UGS Platform**).
