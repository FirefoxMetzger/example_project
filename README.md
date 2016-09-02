# Example Project
This section *must* be included in the project. It is a short description of what this project does.

This is a small example to scetch out we organize libraries and executable code. While this library contains all implementations and definitions necessary, it is not intended that you use or build this code in an isolated environment. Instead, add this as a submodule to the parent project and write a small `FindExampleProject.cmake` to add appropriate dependencies where needed.

It is important to note that this project defines _exactly_ the following two CMake targets:

* **ExampleProject** -- a single library or executable
* **ExampleProjectTest** -- tests for this project

**Dependencies of this project are not included!** There is a simple reason behind this. As many projects may be depending on the same library it would be odd if they all provided it themselfs. As we aim for full source builds, this would mean that each project provides its personal code to compile a library called `foo`. This is both redundant and messy, as there is no guarantee that all `foo`s have the same version or are compatible. Thus to follow the KISS principle, the user has to provide the dependancies via the parent project, defining `Find<Package>.cmake` modules, where `<Package>` is the name of the dependency. Example code for such find modules can be found below.

This repository structure was inspired by [this talk from the BoostCon](https://www.youtube.com/watch?v=3eH4hMKl7XE). While not copying all of the displayed procedures, the idea of one 'all-repo' works really well.

## Table of Content
This section *must* be included in the project. It allows easy navigation inside the readme (either with Ctrl + F or ancors).

1. Directory Organisation
2. Dependencies
3. Installation
4. Contribution
5. Tests
6. FindPackage Example
7. How To Modify Files
8. Top Level File Content

## Dependencies
This section *must* be included in the project. It links to projects / repos this project needs to build successfully.

* [Paddle](https://github.com/baidu/Paddle)
* [bullet3](https://github.com/bulletphysics/bullet3)

## Directory Organisation
This section *may* not be included in the project. It serves a discriptive purpose only.

    doc ----------------- Location of the files to generate the documentation for this project
    h ------------------- Location of the 'private' header files for this project
    include ------------- This can be included by other projects for include files
    ---ExampleProject---- Location of the 'public' header files for this project
    src ----------------- Location of platform independant source files
    ---platform --------- Location of platform specific source files
    test ---------------- Location of the unit tests for this project

## Installation
This section *must* be included in the project. A breef description on how to install this repository.

If you are using a 'meta-repo' strategy:

* at the top level of the repo OR in the ThirdParty folder open a command window
* `git submodule add git@github.com:FirefoxMetzger/example_project.git`
* add a `FindExampleProject.cmake` in `meta_repo/CMakeModules/`
* for each dependency of this project:
  * if the dependency has not been added yet
    * navigate to the project's repository
    * follow instructions on how to add the dependency / install the dependency

If you are using an 'all-repo' strategy:

* at the top level of the repository open a command window
* `git submodule add git@github.com:FirefoxMetzger/example_project.git`
* add a `FindExampleProject.cmake` to `all-repo/CMakeModules/`

Other Repository structures:

Installation highly depends on your project structure. If you have trouble or a suggestion on how to make it more friendly for your environment while not loosing compatibilty with other environments described above, feel free to open or expand on an Issue.

## Contribution
This section *must* be included in every project. Outline how contributions should be made.

As this project serves an example purpose only, there is no strict guideline. If you find a mistake or want to suggest an improvement simply open Issue.

## Tests
This section *must* be included in every project. Describe how to run the tests to verify that this project is working as intended.

There is no code in this repo, thus nothing can be tested (or be broken).

## FindPackage-Example
This section *may* be included in the project. It describes how an `Find<Package>.cmake` might look for this project.

#### file: `FindExampleProject.cmake`
	# finds and imports the ExampleProject

	if(NOT TARGET ExampleProject)
		add_subdirectory(${CMAKE_SOURCE_DIR}/ExampleProject)
	#	add_subdirectory(${CMAKE_SOURCE_DIR}/ThirdParty/ExampleProject)
	endif(NOT TARGET ExampleProject)

	if(TARGET ExampleProject)
		set(ExampleProject_DEFINED TRUE)
	endif()

	include(FindPackageHandleStandardArgs)
	FIND_PACKAGE_HANDLE_STANDARD_ARGS(
		ExampleProject
		FOUND_VAR ExampleProject_FOUND
		REQUIRED_VARS ExampleProject_DEFINED
	)

## How To Modify Files
## Top Level File Content
