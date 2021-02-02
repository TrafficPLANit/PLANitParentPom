# PLANitParentPom

Repository solely in existence to manager the master , a.k.a. parent `pom.xml` from which all child projects of PLANit derive to obtain their dependency versions

### Master pom.xml

The `pom.xml` in this repository is references by all PLANit projects as their parent pom. It contains all the versions for dependencies used to keep them consistent and easy to maintain.

It also contains dependency management and plugin management sections for default configurations of these dependencies and plugins to minimise the configuration in each of the child poms
