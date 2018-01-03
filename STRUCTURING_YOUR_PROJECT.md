# Structuring Your Project

This page outlines good practices for Python based projects, but many of the principles discussed here can be applied to 
other software projects as well.

## Start from a common skeleton which separates key package components

Packages should rely on a common file structure which separates the various elements of a package into separate 
locations. Remember that a package is not just the code needed to carry out science, but also documentation and 
deployment. We recommend the following skeletal file structure for some package `examplepackage`:
 
```
devtools/
  README.md
  travis-ci/
    install_miniconda.sh
  appveyor-ci/
    run_with_env.cmd
  conda-recipe/
    meta.yaml
    build.sh
    bld.bat
    README.md
docs/
examplepackage/
  tests/
    __init__.py
    test_examplepackage.py
  __init__.py
  examplepackage.py
LICENSE.md
README.md
setup.py
.travis.yml
.appveyor.yml
.gitignore
```

This list may appear daunting at first, but each element is either a critical component of what will make the software 
easy to access, and easy to maintain. The following sections will break down each element in the skeleton and explain 
why they are helpful. Your package may not need *every* element of this skeleton, but should include many of them.

## The root directory: Primary setup file, CI control, and Git(Hub) Helpers  

```
LICENSE.md
README.md
setup.py
.travis.yml
.appveyor.yml
.gitignore
```

The root directory should contain the primary `setup.py` file for the `examplepackage`. This is the primary file that 
users and deployment tools will run to build the package. This is a critical component of any Python package and 
should always be included.

The `.travis.yml` and `.appveyor.yml` are the config files needed by Travis (Linux/OSX) and AppVeyor (Windows) 
Continuous Integration (CI) tools which are common to many packages on GitHub. These tools help automatically test 
changes proposed changes, and making sure changes to upstream packages don't break the existing code. We cover CI 
tools in more detail 
[in a later chapter][CI_page].
If a package is not deployed on a specific OS, or runs a different CI tool, these specific files may not be present, 
but some type of CI should be included so the developer does not need to manually run the tests themsvels.

The final three files, `LICENSE.md`, `README.md` and `.gitignore` are Git and GitHub specific files which should 
always be included. The `LICENSE.md` file is a direct copy of the 
[licensing][license_page] the package 
falls under. GitHub can detect most common licenses from this file automatically and add the front page of the 
project with this information (as shown as the red box in the image below).

![The license file is automatically detected by GitHub][license_highlight]

The `README.md` file is the *most important file* for a GitHub project. A Markdown file with this name is rendered 
by GitHub on the project's homepage. That means this is the **FIRST** thing users see when visiting `exampleproject`, 
so this should be an informative file which tells users the following:
1. Short explanation of what the project does
1. Quick "How-To install and run" the project. This should be only a few lines, which is why its important to 
   ensure the project can be installed easily.
   * This topic is covered [in a later chapter][package_deploy_page], but its important to plan for this section now
1. Who the authors of the package are
1. Where to read the full documentation

The `README.md` is not the place to dump all the documentation for the package for most packages, but it should 
inform the users how to access all the needed info. More info on good `README.md` files can be found 
[in a later chapter][documentation_page].

The final file in the root directory is the `.gitignore` file which tells `git` (not GitHub) file patterns to ignore 
when adding files to the repository, one per line. This is helpful for preventing accidental file additions such as 
compiled Python binaries `.pyc` files with the simple pattern `*.pyc`. There is no "master" list for every project, 
but [GitHub has some handy templates][gitignore_template] packages can borrow. This is not a required file, but will 
make software development much easier by reducing the number of accidental file commits.

## Documentation files should be in their own directory

```
docs/
```

All documentation files should be kept separate from the main project code whenever possible. These are separate 
from code documentation in the main package files, and should be able to compile the docs separate from the main code.
Please read [the entire chapter we dedicated to this topic][documentation_page] for more information. 
 
## Deployment and CI tools should be separate from the main code

```
devtools/
  README.md
  travis-ci/
    install_miniconda.sh
  appveyor-ci/
    run_with_env.cmd
  conda-recipe/
    meta.yaml
    build.sh
    bld.bat
    README.md
```

The `devtools` directory is a place to store deployment and CI tools. The name of the directory is arbitrary, but 
should be very distinct from the project files and the docs; we find "`devtools`" name to be distinct enough. 
The content of this directory will differ from package to package because of deployment method, CI tools, and 
documentation building. However, every `devtools` directory should have its own `README.md` file which will be 
rendered on GitHub explaining the content of the directory and how to use the files within.
This example assumes `conda` deployment with both Travis and AppVeyor CI tools.

The `travis-ci` and `appveyor-ci` folders are arbitrary names, but contain the scripts that the `.travis.yml` and 
`.appveyor.yml` respectively call to do more complex scripts that are difficult to call with the YAML file each 
CI tool reads. For instance, installing Miniconda, configuring Visual Studio, downloading external libraries 
to compile again, or deploying compiled docs to an external server. The directory contents will differ and there 
are no mandatory file names, but file names should be descriptive.

The `conda-recpie` directory is also an arbitrary name, but contains the files needed to do a `conda` deployment 
on the operating systems. We have [an entire chapter for deployment][package_deploy_page] and will not go into 
further details here.

## Core package files should include tests

```
examplepackage/
  tests/
    __init__.py
    test_examplepackage.py
  __init__.py
  examplepackage.py
```

The example package software files should all exist in their own directory from the root directory. We recommend 
calling this directory the same name as the package for clarity, hence the `examplepackage` top directory. 
Within this directory are all the required software file, in this example is just the package's `__init__.py` file, 
and the single package file `examplepackage.py`. Most package will have many more modules and files, but we only 
show one for this example.

The `tests` directory should be a staple of any package, and more importantly included with the package source code. 
Tests are just as important as the package itself as it ensures that code functions and gives the CI tools 
something to run to verify changes do not break something. Please consider 
[reading our dedicated chapter to unit tests][unit_test_page] for more information.

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!

|__Previous:__||__Next:__|
|:---|---|---:|
|[Licensing Guidelines](https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md)|[Back to Top](https://github.com/choderalab/software-development/blob/master/README.md)|[Version Control](https://github.com/choderalab/software-development/blob/master/VERSION_CONTROL.md)|

[license_highlight]: https://github.com/choderalab/software-development/raw/master/chapter_images/structure_license_highlight.png "Highlighted license"
[license_page]: https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md
[package_deploy_page]: https://github.com/choderalab/software-development/blob/master/LICENSING_GUIDELINES.md
[CI_page]: https://github.com/choderalab/software-development/blob/master/CONTINUOUS_INTEGRATION.md
[gitignore_template]: https://github.com/github/gitignore/blob/master/Python.gitignore
[documentation_page]: https://github.com/choderalab/software-development/blob/master/DOCUMENTATION.md
[unit_test_page]: https://github.com/choderalab/software-development/blob/master/UNIT_TESTING.md