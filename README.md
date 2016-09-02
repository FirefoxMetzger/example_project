# Example Project

This is a small example to scetch out we organize libraries and executable code. While this library contains all implementations and definitions necessary, it is not intended that you use or build this code in an isolated environment. Instead, add this as a submodule to the parent project and write a small `Find<Package>.cmake` to add an appropriate target dependencies where needed.

**Dependencies of this project are not included!** There is a simple reason behind this. As many projects may be depending on the same library it would be odd if they all provided it themselfs. As we aim for full source builds, this would mean that each project provides its personal code to compile a library called `foo`. This is both redundant and messy, as there is no quarantee that all `foo`s have the same version or are compatible. Thus to follow thie KISS principle, the user has to provide the dependancies via the parent project, defining `Find<Package>.cmake` modules, where `<Package>` is the name of the dependency. Example code for such find modules can be found below.

This repository structure was inspired by [this talk from the BoostCon](https://www.youtube.com/watch?v=3eH4hMKl7XE). While not copying all of the displayed procedures, the idea of one 'all-repo' works really well.

## Table of Content



## Directory-Organisation
## Installation
## Contribution
## Tests
## FindPackage-Example
## How-to-modify-files
## The-Top-Level
