Scala for OpenShift - Docker images
========================================

This repository contains the source for building various versions of
the Scala application as a reproducible Docker image using
[source-to-image](https://github.com/openshift/source-to-image).
The resulting image can be run using [Docker](http://docker.io).


Versions
---------------
Scala versions currently provided are:
* SBT 0.13

Java versions currently provided are:
* Java 1.8.0

CentOS versions currently supported are:
* CentOS 7


Installation
---------------

*  **CentOS based image**

    To build a Scala image from scratch run:

    ```
    $ git clone https://github.com/ticketfly/sti-scala.git
    $ cd sti-scala/sbt-0.13-java-8
    $ make build
    ```


Usage
---------------------
To build a simple [Scala-sample-app](https://github.com/pat2man/play-originv3-test) application
using standalone [STI](https://github.com/openshift/source-to-image) and then run the
resulting image with [Docker](http://docker.io) execute:

*  **For CentOS based image**
    ```
    $ s2i build https://github.com/ticketfly/sti-scala.git --context-dir=sbt-0.13-java-8/test/test-app/ ticketfly/sbt-0.13-java8-centos7 scala-test-app
    $ docker run -p 9000:9000 scala-test-app
    ```

**Accessing the application:**
```
$ curl 127.0.0.1:9000
```


Test
---------------------
This repository also provides a [S2I](https://github.com/openshift/source-to-image) test framework,
which launches tests to check functionality of a simple Scala application built on top of the sti-Scala image.

Users can choose between testing a Scala test application based on a RHEL or CentOS image.


*  **CentOS based image**

    ```
    $ cd sti-scala/sbt-0.13-java-8
    $ make test
    ```
