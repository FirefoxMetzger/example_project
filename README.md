# Example Project
This section *must* be included into every project

This is a small example to scetch out we organize libraries and executable code. While this library contains all implementations and definitions necessary, it is not intended that you use or build this code in an isolated environment. Instead, add this as a submodule to the parent project and write a small `FindExampleProject.cmake` to add appropriate dependencies where needed.

It is important to note that this project exports _exactly_ the following two CMake targets:

* **ExampleProject** -- a single library or executable
* **ExampleProjectTest** -- tests for this project

**Dependencies of this project are not included!** There is a simple reason behind this. As many projects may be depending on the same library it would be odd if they all provided it themselfs. As we aim for full source builds, this would mean that each project provides its personal code to compile a library called `foo`. This is both redundant and messy, as there is no guarantee that all `foo`s have the same version or are compatible. Thus to follow the KISS principle, the user has to provide the dependancies via the parent project, defining `Find<Package>.cmake` modules, where `<Package>` is the name of the dependency. Example code for such find modules can be found below.

This repository structure was inspired by [this talk from the BoostCon](https://www.youtube.com/watch?v=3eH4hMKl7XE). While not copying all of the displayed procedures, the idea of one 'all-repo' works really well.

## Table of Content

1. Directory Organisation
2. Dependencies
3. Installation
4. Contribution
5. Tests
6. FindPackage Example
7. How To Modify Files
8. Top Level File Content

## Dependencies

## Directory Organisation
This section *may* not appear in a real code repository. It serves a discriptive purpose only.

    doc ----------------- Location of the files to generate the documentation for this project
    h ------------------- Location of the 'private' header files for this project
    include ------------- This can be included by other projects for include files
    ---ExampleProject---- Location of the 'public' header files for this project
    src ----------------- Location of platform independant source files
    ---platform --------- Location of platform specific source files
    test ---------------- Location of the unit tests for this project

## Installation
If you are using a 'meta-repo' strategy:

* at the top level of the repo OR in the ThirdParty folder open a command window
* `git submodule add git@github.com:FirefoxMetzger/example_project.git`
* add a `FindExampleProject.cmake` in `meta_repo/CMakeModules/`

If you are using an 'all-repo' strategy:

* at the top level of the repository open a command window
* `git submodule add git@github.com:FirefoxMetzger/example_project.git`
* add a `FindExampleProject.cmake` to `all-repo/CMakeModules/`

Other Repository structures:

This really comes down to how you personally want to organise it

## Contribution
## Tests
## FindPackage-Example
## How To Modify Files
## Top Level File Content
