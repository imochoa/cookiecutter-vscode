# How-to

## Required VSCode extensions
- [CppTools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- `.vscode/c_cpp_properties.json` can help save some conguration parameters (include paths, compiler, ...)

## [tasks.json](.vscode/tasks.json)
Used for [integrating with external build tools](https://code.visualstudio.com/docs/editor/tasks)

Here is the [tasks.json schema](https://code.visualstudio.com/docs/editor/tasks-appendix)

The default task should work for basic `cpp` programs

### Modifying compilation arguments

The default task should work for standalone `cpp` programs. 
However, you might have to modify the `"args"` to build your program.

Just play around with the compilation command on the command line until you get it working and then transfer the compilation arguments to the `"args"` list

Here's an example:
```json
{
	"command": "/usr/bin/g++",
	"args": [
		"-fdiagnostics-color=always",
		"-I",
		"${fileDirname}",
		"-I",
		"/usr/include/eigen3",
    "-I",
		"/path/to/some/include",       
		"-g",
		"${file}",
    "/path/to/file1.cpp",
    "/path/to/file2.cpp",
		"-o",
		"${fileDirname}/${fileBasenameNoExtension}"
		"-lHalf",
		"-ltbb",
    "-lyourlib"
	]
}
```

#### Libraries
Remember that for libraries, you don't have to write the full name, eg `libtbb` would be `-ltbb`.
You can find the available libraries name by running `ldconfig -p`


## [launch.json](.vscode/launch.json)
For [running/debugging in VSCode](https://code.visualstudio.com/docs/editor/debugging). There's also a [cpp-specific launch.json overview](https://code.visualstudio.com/docs/cpp/launch-json-reference).

For compiled languages, it is important to set the launch config's `"preLaunchTask"` to match the `"label"` of the task you set up in the [tasks.json](.vscode/tasks.json). Pay attention to any dependencies between them
> For example the fact that the build **task** will generate a name for the binary executable based on the current file's name using some rule: `"${fileDirname}/${fileBasenameNoExtension}"`
>
> This rule is DUPLICATED in the **launch config** and is required to run the task's output!

### Modifying the run/debug arguments
If you want to give the executable any arguments, you can specify that using the launch config's `"args"` list.

You might want to consider duplicating the launch config to keep track of all of the different "input scenarios" instead of overwritting the one-and-only launch config every time you want to try something new.

Here's an example:
```json
{
    "args": ["-i","/path/to/input","-o","/path/to/output"],
}
```

## [settings.json](.vscode/settings.json)
General configuration settings [More info here](https://code.visualstudio.com/docs/getstarted/settings#_settingsjson)

### [Settings editor](https://code.visualstudio.com/docs/getstarted/settings#_settings-editor)
You can also open the Settings editor by:
- File > Preferences > Settings
- from the Command Palette (Ctrl+Shift+P) with "Preferences: Open Settings" 
- use the keyboard shortcut (Ctrl+,).


# Cookiecutter ToDo's
- Use more params (like maybe {{cookiecutter.compiler}}, {{cookiecutter.includes}}, {{cookiecutter.libraries}}, etc)

