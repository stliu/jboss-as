This readme contains information about building and testing EAP.

Building
---------
To run a basic EAP build from the root directory of AS:

./build.sh

This build will only use the Mead (product) Maven repository which does not include 
all the necessary dependencies for running the testsuite.  This will also create a 
local maven repository called "local-repo-eap".

Testing
-------
The full testsuite can be run from the root directory using the "allTests" property:

./build.sh -DallTests

This will run the full testsuite and will activate the public Maven repositories
(central and jboss.org) which are required to build and run the testsuite.
All dependencies will be downloaded to the local directory "local-repo-eap".

To run only a specific testsuite module or an individual test, you will still need
to run build.sh from the root directory.  Individual testsuite modules can be run
by setting the directory using the "-pl" option.  The basic integration tests can
be run using this option.

./build.sh -DallTests -pl testsuite/integration/basic

A slightly simpler command can be run from within the testsuite directory.

./build.sh -pl integration/basic

To run a single test, use the -Dtest option to Maven
From the root directory:

./build.sh -DallTests -pl testsuite/integration/basic -Dtest=XercesUsageTestCase

Or from the testsuite diretory:
./build.sh -pl integration/basic -Dtest=XercesUsageTestCase


