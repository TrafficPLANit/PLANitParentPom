# PLANitParentPom

Repository solely in existence to manager the master , a.k.a. parent `pom.xml` from which all child projects of PLANit derive to obtain their dependency versions

> In Git we explicitly ignore all root irectories starting with PLANit\*, this is to facilitate using the parentpom project as a git submodule and subsequent other PLANitX
repositories (and possible external extensions) as subdirs using this naming convention. In ignoring these directories we ensure that upon committing the ParentPom repo module won't be
flagged as dirty potentially causing the user to commit the subdirs as part of this repo which should never be done.

## Master pom.xml

The `pom.xml` in this repository is references by all PLANit projects as their parent pom. It contains all the versions for dependencies used to keep them consistent and easy to maintain.

It also contains dependency management and plugin management sections for default configurations of these dependencies and plugins to minimise the configuration in each of the child poms

## Git Branching model

We adopt GitFlow as per https://nvie.com/posts/a-successful-git-branching-model/
