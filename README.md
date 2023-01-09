# CppCheck
Cppcheck is a static analysis tool for C/C++ code.

Install
---
Commands to install cppcheck and cppcheck-gui on Linux
```
sudo apt-get install cppcheck
sudo apt-get install cppcheck-gui
```

Commands
---
Command | Description
--- | ---
--help | Display help
--xml | Generate output as xml format
--output-file=\<file> | Output file name
--std=\<std> | C++/C standard tp use. eg --std=c++20
--language=\<language> | Force to use c++/c language on all files
--enable=\<checks> | Enable types of checks to perform

The above table list only few options. For complete details use cppcheck --help

```
cppcheck --enable=all --language=c++ --std=c++20 --output-file=out.txt <path_to_cpp_files>
```
All cpp files and included h files by them are checked recursively in all the folders.

Links
---
Website - https://cppcheck.sourceforge.io/ <br/>
Github - https://github.com/danmar/cppcheck/
