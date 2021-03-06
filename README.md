![Logo](https://avatars3.githubusercontent.com/u/30268214?v=4&s=200)
[![Build Status](https://travis-ci.org/AlloyTools/org.alloytools.alloy.svg?branch=master)](https://travis-ci.org/AlloyTools/org.alloytools.alloy)
# Alloy

Alloy 4 is a self-contained executable, which includes the Kodkod
model finder and a variety of SAT solvers, as well as the standard
Alloy library and a collection of tutorial examples. The same jar file
can be incorporated into other applications to use Alloy as an API,
and includes the source code. See the release notes for details of new
features. 

More documentation can be found at: http://alloy.mit.edu/alloy/documentation.html.

# TL;DR

Checkout the project and type ./gradlew. You find the executable JAR in org.alloytools.alloy.dist/target/org.alloytools.alloy.dist.jar after the build has finished.

     $ java version           # requires 1.8 (and NOT 1.9, gradle does not run on 1.9)
     java version "1.8.0_144"
     Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
     Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed model
     $ git clone git@github.com:AlloyTools/org.alloytools.alloy.git
     $ cd org.alloytools.alloy
     $ ./gradlew build
     $ java -jar org.alloytools.alloy.dist/target/org.alloytools.alloy.dist.jar
     # opens GUI

## Building Alloy

The Alloy build is using a _bnd workspace_ setup using a maven layout. This means it can be build  with Gradle and  the Eclipse IDE for interactive development. Projects are setup to continuously deliver the executable.

### Projects

The workspace is divided into a number of projects:

* [cnf](cnf) – Setup directory. Dependencies are specified in [cnf/central.xml] using the maven POM layout
* [org.alloytools.alloy.application](org.alloytools.alloy.application) – Main application code includes the parser, ast, visualiser, and application code
* [org.alloytools.alloy.dist](org.alloytools.alloy.dist) – Project to create the distribution executable JAR
* [org.alloytools.alloy.extra](org.alloytools.alloy.extra) – Models and examples
* [org.alloytools.kodkod.core](org.alloytools.kodkod.core) – Kodkod without native code
* [org.alloytools.kodkod.native](org.alloytools.kodkod.native) – The native code libraries for kodkod

### Relevant Project files

This workspace uses bnd. This means that the following have special meaning:

* [cnf/build.xml](cnf/build.xml) – Settings shared between projects
* ./bnd.bnd – Settings for a project. This file will _drag_ in code in a JAR.
* [cnf/central.xml](cnf/central.xml) – Dependencies from maven central

### Eclipse

The workspace is setup for interactive development in Eclipse with the Bndtools plugin. Bndtools can be installed from the [Eclipse Market](https://marketplace.eclipse.org/content/bndtools) place (see `Help/Marketplace` and search for `Bndtools`). 

Bndtools will continuously create the final executable. The projects are setup to automatically update when a downstream project changes.

### Gradle 

In the root of this workspace type `./gradlew`. This is a script that will download the correct version of gradle and run the build scripts. For settings look at [gradle.properties] and [settings.gradle].

### Continuous Integration

The workspace is setup to build after every commit using Travis. It releases snapshots to `https://oss.sonatype.org/content/repositories/snapshots/org/alloytools/` for every CI build on Travis.

### Building the DMG file for OSX systems

Currently only the executable jar in org.alloytools.alloy.dist/target/org.alloytools.alloy.dist.jar is build. In the `org.alloytools.alloy.dist` project, run `../gradlew macos`. This will leave the PKG file in `target/bundle`.

## CONTRIBUTIONS

Please read the [CONTRIBUTING](CONTRIBUTING.md) to understand how you can contribute.

[javapackager]: https://docs.oracle.com/javase/8/docs/technotes/guides/deploy/packager.html
