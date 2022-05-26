# PLANitParentPom
![Master Branch](https://github.com/TrafficPLANit/PLANitPArentPom/actions/workflows/maven_master.yml/badge.svg?branch=master)
![Develop Branch](https://github.com/TrafficPLANit/PLANitPArentPom/actions/workflows/maven_develop.yml/badge.svg?branch=develop)

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

## Maven and Eclipse - a quick introduction

The following notes explain how to run Maven builds for projects (using this parent pom) in Eclipse.

Firstly, ensure that you are using a version of Eclipse which has the Maven plugin built in.  Most current versions of Eclipse include Maven.  If you are unsure, select File/New/Other.. and look at the list of available wizards which appears.  If there is a folder called "Maven" which includes a link called "Maven Project", Maven is included.

Right-click on the PLANit project in the Package Explorer and select Run As.  You will see a drop-down menu.  Often you can just click "Maven Install" and it will work, since it performs the following actions:-

* Collects dependencies
* Compiles the Java code;
* Runs the unit tests.

The results of the unit tests appear in the Console.  The "BUILD SUCCESS" message only appears if all the unit tests pass, which is usually what you want.

However there may be times when you do not wish to perform all these steps at once.  For example, you may have made some temporary changes which cause the unit tests to fail, and you just want to compile the code without them.  

The drop-down menu has other useful options, including:-

* "Maven clean", which removes previously-created .class files from the target directory.

However the most configurable approach is to click the "Run Configurations.." and use the resulting dialog box, as follows:-

* Select "Maven Build" from the left window on the dialog box, and then click the "New Configuration" icon at the top-left of the dialog box.  This brings up a configuration window in the right-hand side of the dialog box;
* Use the "Name" box at the top to enter a name for the configuration.  This can be anything which makes sense to you.  I recommend "Maven clean install" if you follow the steps below;
* Use the "Workspace..." button under the "Base directory" box to select the project you wish to compile (e.g. PLANit, PLANitXML etc);
* Enter whichever Maven goals you want to use in the "Goals" box.  If you know nothing about Maven goals, I recommend entering "clean install" in this box (Maven goals is a large topic, see the Maven documentation for more details).

Leave the other entries at their defaults in the first instance, and click Run.  This will perform the build and run as above.  

The Run Configuration dialog box disappears as the run begins, but the configuration is still saved.  If you right-click the project and select Run/Run Configuration... again, you will see the configuration you just created under the "Maven Build" heading in the left window. You can click on it and run it again as you require.

You can change the configuration at any time as required by your code changes.  Two changes which are particularly useful are:

* Use the "Workspace" button under the "Base directory" box to change which project you are running;
* Checking or unchecking the "Skip test" box can stop or reinstate unit tests being run as part of the build.

Whenever you click Run, the configuration dialog box closes.  Its setting on its closure will be retained for the next time it is opened.  If you use this dialog box often on several projects, do not forget to check its settings on opening are appropriate for the build you are doing.

It is a matter of personal taste whether you run unit tests directly (by right-clicking on a test suite and selecting Run As/JUnit Test) or run them as part of this build process.  Running them directly will not generate Java classes from XSD files, so if you have made changes to the XSD files you must rebuild.  Running directly is fractionally quicker, but the builds only take a few seconds so the difference is negligible.


## Git Branching model

We adopt GitFlow as per https://nvie.com/posts/a-successful-git-branching-model/
