# PLANitParentPom

Repository solely in existence to manager the master , a.k.a. parent `pom.xml` from which all child projects of PLANit derive to obtain their dependency versions

> In Git we explicitly ignore all root irectories starting with PLANit\*, this is to facilitate using the parentpom project as a git submodule and subsequent other PLANitX
repositories (and possible external extensions) as subdirs using this naming convention. In ignoring these directories we ensure that upon committing the ParentPom repo module won't be
flagged as dirty potentially causing the user to commit the subdirs as part of this repo which should never be done.

## Master pom.xml

The `pom.xml` in this repository is references by all PLANit projects as their parent pom. It contains all the versions for dependencies used to keep them consistent and easy to maintain.

It also contains dependency management and plugin management sections for default configurations of these dependencies and plugins to minimise the configuration in each of the child poms

## Deployment

Distribution management is setup in this parent pom such that Maven can deploy child builds appropriately. To do so ensure that you setup your credientials correctly in your settings.xml as otherwise any upload will fail.

## PLANit Maven remote repository use

All PLANit child projects pom gain a repository entry defined in this pom that specifies where to find other PLANit projects. This way, you can check out one child project and work on it and Maven will collect its PLANit dependencies automatically via the configured PLANit repository given that the used version is available.

## Git Branching model

We adopt GitFlow as per https://nvie.com/posts/a-successful-git-branching-model/
