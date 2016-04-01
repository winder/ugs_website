# Project Organization

Universal Gcode Sender uses [Maven](http://maven.apache.org/) to build the
project. It is using maven modules to separate the core library / classic GUI
and the UGS Platform project. At the top level a `UGS` target defines the
`ugs-core` and `ugs-platform-parent` modules which can be built separately or
all at once.

The classic gui is part of the core project in the `ugs-core` module. The
`maven-shade-plugin` and `maven-assembly-plugin` are generate the
self-executing JAR and distribution zip.

UGS Platform is built on the [NetBeans Platform](https://netbeans.org/features/platform/).
It is also using maven.

Development is done using NetBeans, but most of the code can be edited using
any IDE that supports Maven.

# Development with an IDE
----------------

Any IDE supporting Maven should be able to open the UGS project directory. Once
opened it should show you the `ugs-core` and `ugs-platform-parent` modules
which correspond to the Classic and Platform interfaces.

Development is done using NetBeans, and for some project development NetBeans
is almost required. But for tweaking the UI and experimenting with the backend
any IDE which supports maven can be used.

## Classic GUI
----------------
In the `ugs-core` module, you can run the `MainWindow.java` file to start the
Classic GUI.

## UGS Platform
----------------
The platform build has a number of submodules. Load the suite of modules by 
running the ugs-platform-app module.

# Development with the Command Line
----------------

The UGS Classic and Platform interfaces can also be run from the command line.
These commands should be run from the root directory.

## Classic GUI
----------------
There is a helper script named `run_classic.sh`, or you can use the commands below.

### Running the UI
```
mvn install
mvn exec:java -Dexec.mainClass="com.willwinder.universalgcodesender.MainWindow" -pl ugs-core
```

### Executing tests
```
mvn install
mvn test -pl ugs-core
```

### Building the self-executing JAR
```
mvn install
mvn package -pl ugs-core
```

### Building a UniversalGcodeSender.zip release file
```
mvn package assembly:assembly
```

## UGS Platform
----------------
There is a helper script named `run_platform.sh`, or you can use the commands below.

### Running the UI
```
mvn install
mvn nbm:run-platform -pl ugs-platform/application
```
