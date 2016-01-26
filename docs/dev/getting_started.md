# Compiling

## Classic GUI

For development the [Maven](http://maven.apache.org/) tool is used. The `maven-shade-plugin` and `maven-assembly-plugin` are used to generate the self-executing JAR and distribution zip.

### Running from the command line
```
mvn exec:java -Dexec.mainClass="com.willwinder.universalgcodesender.MainWindow"
```

### Executing tests
```
mvn test
```

### Building the self-executing JAR
```
mvn package
```

### Building a UniversalGcodeSender.zip release file
```
mvn package assembly:assembly
```


The Classic GUI uses Maven along with 

## UGS Platform

The build process for the platform is not quite as streamlined as the classic project. If for any reason these instructions aren't working, you can refer to the `after_success` commands in `.travis.yml`.

The UGS Platform uses the same backend as the Classic GUI, so that JAR must be built first. The JAR is then copied into the UGSPlatform project at which point ant commands can be used to run the project.
```sh
mvn package assembly:assembly
mkdir -p UGSPlatform/UGSLib/release/modules/ext/ugs/
cp target/UniversalGcodeSender.jar "UGSPlatform/UGSLib/release/modules/ext/ugs/Universal G-Code Sender.jar"
cd UGSPlatform
```

At this point you can use ant to run and build the project.

### Running from the command line
```
ant run
```

### Building a distribution zip
```
ant build-zip
```
