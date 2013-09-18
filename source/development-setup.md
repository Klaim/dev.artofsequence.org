# Development Setup

You'll read below all the instructions to setup a developpement environnement to build and develop Art Of Sequence  projects, mostly C++ ones. Other projects don't need such setup but installing [Python](http://www.python.org/) for scripts.

## 0. Programming Languages

 * Most tools are implemented in **modern C++**, using **Boost**.
 * For GUI in C++ we use **Qt** by default (this will change in the future).
 * For scripts and raw developers tools (files and texts manipulation) we use [**Python**](http://www.python.org/).
 * Some projects requires **HTML/CSS/Javascript** coding, like the [AOS Web Player](https://github.com/artofsequence/aos-webplayer).

## 1. Dependencies

There are some dependencies required to compile all the projects:

 * [Boost >= 1.54.0](http://www.boost.org/) 
 * [Qt 5.x SDK](http://qt.nokia.com/) : should be automatically found by CMake. Used in AOS Designer project for GUI.
 * [CodeSynthesis XSD 3.2.0](http://www.codesynthesis.com/products/xsd/) : Have to be installed on the system. Used in [AOSLCPP](https://github.com/artofsequence/aosl-cpp) project to implement AOSL model in C++.
 * [Python](http://python.org/) : Python have to be available in the environnement. It's used mostly for scripts manipulating files and text, but it could be used for tools implementation too. 
 * [Some other dependencies](https://github.com/artofsequence/aos-all-dependencies) which we provide a version in this repository but you could get them yourself too.
 

## 2. Projects Generation

You'll need to install [CMake](http://www.cmake.org/) on your system if not already. We use CMake 2.8 or superior (compatible) version.

Using CMake you can generate the whole solution of the project for your preferred IDE or compiler. *Note that the main development of the project is made using Visual Studio 2010/2012 with the Qt Visual Addin extension, so other IDE and platform aren't tested yet. Please report any problem with other setup.*

To generate the whole solution, use CMake in the root directory of the repository. It should find automatically all the dependencies.

No configuration flags should be required to generate the project but if some dependencies aren't found, then you should manually setup the paths to the dependencies folders.

**All the projects binaries will be gathered in the /Build/Configuration/ directory of the project**, but replace "Configuration" by the configuration "Debug", "Release" or other configurations.

**Notes if you're using Visual Studio** : 

 * You might want to add /MP in the COMPILER_FLAGS variable to allow VC to do parallel compilation of non-dependent projects.
 * **For debugging, setup the execution directory in the binary directory!** CMake will not do it for you and you will have crashes by default when trying to debugging because the default current directory in debug mode will be the project file directory instead of the binary directory! If you generate the solution in the repository root directory, then you should put `"$(SolutionDir)\Build\$(Configuration)\"` in the `Project>Properties>Debugging>Working Directory` field, for all configurations.



**Once you've compiled all the projects**, don't forget :

 * if you want to add or remove files : 
  * add/remove the file names in CMakeFiles.txt
  * regenerate the project using CMake
 * projects depending on Qt needs to generate special code that CMake will generate for you, so don't forget to make sure that your Q_OBJECT classes are processed by the Qt pre-processor ([see AOS Designer CMakeFiles.txt for examples](https://github.com/artofsequence/aos-designer/blob/master/CMakeLists.txt))

## 3. Code Generation

Note: this part will be moved to the AOSLCPP wiki soon.

Some projects have code generated from other sources. If you modify those sources, make sure to generate the code from it, then check that everything still work, maybe make some modifications/fixes, then commit the generated files too. 

At the moment, the main source of code generation is the [AOSL xsd definition file](http://artofsequence.org/aosl/). It is used to generate most of the AOSLCPP project sources. If you need to modify the language definition proceed through those steps :

 * Change the [xsd file](https://github.com/artofsequence/aosl/blob/master/aosl.xsd) to match your language change.
 * [Execute the python script available in the "script" folder](https://github.com/artofsequence/aosl-cpp/blob/master/script/generate_cpp.py) to generate the C++ code equivalent of the xsd definition.
 * Compile and fix AOSLCPP and maybe add new library features accordingly to your changes.
 * Compile projects that depends on AOSLCPP like AOS Designer to make sure everything is fine.


## 4. Contributions

 * [Please read the coding standard for the projects before starting implementations.](Coding-Standard)
 * [There is a non-exhaustive list of fronts that need contributions available there.](How-To-Contribute)