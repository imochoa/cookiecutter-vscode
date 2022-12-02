# How-to

## Required VSCode extensions
- [CppTools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [CMakeTools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
- `.vscode/c_cpp_properties.json` can help save some conguration parameters (include paths, compiler, ...)

## [CMakeTools on Linux](https://code.visualstudio.com/docs/cpp/cmake-linux)

Steps:
- Palette (Ctrl+Shift+P) and run the `CMake: Quick Start` command:
- Open the Command Palette (Ctrl+Shift+P) and run `CMake: Select a Kit`
- To select a variant (Debug/Release/...), open the Command Palette (Ctrl+Shift+P) run the `CMake: Select Variant` command
- open the Command Palette (Ctrl+Shift+P) and run the `CMake: Configure` command to configure your project. This generates build files in the project's build folder using the kit and variant you selected.
- open the Command Palette (Ctrl+Shift+P) and run the `CMake: Build command`, or select the Build button from the Status bar.
> You can select which targets you'd like to build by selecting CMake: Set Build Target from the Command Palette. By default, CMake Tools builds all targets. 
> The selected target will appear in the Status bar next to the Build button (at the bottom of the screen)
-  (Ctrl+Shift+P) and run `CMake: Debug`


[How To Use VS CODE for C++ | With CMake & Any Compiler](https://www.youtube.com/watch?v=gGxi500Q5uE)


https://cliutils.gitlab.io/modern-cmake/chapters/intro/running.html

cmake --build build --verbose # CMake 3.14+ only

--trace-source="filename"


# [How to structure your project](https://cliutils.gitlab.io/modern-cmake/chapters/basics/structure.html)

First, this is what your files should look like when you start if your :
- project is creatively called project
- with a library called lib
- and a executable called app:


You often want a cmake folder, with all of your helper modules. This is where your Find*.cmake files go. An set of some common helpers is at github.com/CLIUtils/cmake. To add this folder to your CMake path:


[A simple example](https://cliutils.gitlab.io/modern-cmake/chapters/basics/example.html)

[Complete example](https://gitlab.com/CLIUtils/modern-cmake/tree/master/examples/simple-project)