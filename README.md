jpy - a Python-Java Bridge
jpy is a bi-directional Python-Java bridge which you can use to embed Java code in Python programs or the other way round. It has been designed particularly with regard to maximum data transfer speed between the two languages. It comes with a number of outstanding features:

Fully translates Java class hierarchies to Python
Transparently handles Java method overloading
Support of Java multi-threading
Fast and memory-efficient support of primitive Java array parameters via Python buffers (e.g. Numpy arrays)
Support of Java methods that modify primitive Java array parameters (mutable parameters)
Java arrays translate into Python sequence objects
Java API for accessing Python objects (jpy.jar)
jpy has been tested with Python 3.4–3.8 and OpenJDK 8 on 64-bit Ubuntu Linux, Windows 10, and macOS.

The initial development of jpy was driven by the need to write Python extensions to an established scientific imaging application programmed in Java, namely the SNAP toolbox, the SeNtinel Application Platform project, funded by the European Space Agency (ESA). (jpy is bundled with the SNAP distribution.)

Writing such Python plug-ins for a Java application usually requires a bi-directional communication between Python and Java since the Python extension code must be able to call back into the Java APIs.

For more information please have a look into jpy's

documentation
source repository
issue tracker
How to build wheels for Linux and Mac
Install a JDK 8, preferably the Oracle distribution. Set JDK_HOME or JPY_JDK_HOME to point to your JDK installation and run the build script:

$ export JDK_HOME=<your-jdk-dir>
$ export JAVA_HOME=$JDK_HOME
$ python setup.py build maven bdist_wheel
On success, the wheel is found in the dist directory.

To deploy the jpy.jar (if you don't know why you need this step, this is not for you)::

$ mvn clean deploy -DskipTests=true
How to build a wheel for Windows
Set JDK_HOME or JPY_JDK_HOME to point to your JDK installation. You'll need Windows SDK 7.1 or Visual Studio C++ to build the sources. With Windows SDK 7.1::

> SET VS90COMNTOOLS=C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\Tools\
> SET DISTUTILS_USE_SDK=1
> C:\Program Files\Microsoft SDKs\Windows\v7.1\bin\setenv /x64 /release
> SET JDK_HOME=<your-jdk-dir>
> python setup.py build maven bdist_wheel
With Visual Studio 14 and higher it is much easier::

> SET VS100COMNTOOLS=C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\
> SET JDK_HOME=<your-jdk-dir>
> python setup.py build maven bdist_wheel
