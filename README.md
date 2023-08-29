# C++ at the University of Manchester: quickstart guide

This guide contains instructions on how to set up your laptop for coding, compiling and running C++ programs. 

## Instructions if you bring your own laptop 

### Mac 

#### Installing an editor / IDE on a mac

If you have a mac, you can install the Visual Studio Code IDE with a g++ compiler as back-end.
You can use visual studio code (https://code.visualstudio.com) as a mac package; an open source IDE that is in very common use with the gcc11 compilers. 
You can also install the desktop C++ development option as this will give you several helpful tips while writing your code. 
Visual Studio Code is straightforward to install, but setting up the compilers is slightly more complex: please read on.

Important note: on a mac, it's better to not use XCode as a development platform or clang as a compiler, as this leads to different error messages with respect to those using g++.

#### Installing a compiler on mac

##### Homebrew installation 

Open a terminal window, and copy one of the two following into into a terminal window:

For MacOS Catalina, macOS Mojave, and MacOS Big Sur and MacOS Monterey:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

For macOS High Sierra, Sierra, El Capitan, and earlier:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##### XCode requirements

Then, let the installation program install what you need from xcode. 

In a terminal window, type:

```
xcode-select --install
```

(we also remind you not to use XCode as a development platform as it generally comes with clang)

Note: it's better to uninstall/reinstall xcode to make sure you have the most recent version. 
You can do that with:

```
sudo rm -rf /Library/Developer/CommandLineTools
xcode-select --install
```
(this is for users that don't usually do much with CommandLineTools and have no special configuration - take care and do backup anything you'd like to keep or port if you're not in this category!)

##### gcc/g++ from homebrew 

Then, install the gcc/g++ suite from homebrew:

In a terminal window, type:

```
brew install  gcc@11
```

It may take a while for it to complete, but at the end you should have the following file (check in a terminal with "ls" if you do have it, and it doesn't return that it doesn't find the file):

```
/usr/local/bin/g++-11
```

In more recent version of homebrew, you may find this file in a different brew directory, e.g. /usr/local/Cellar/ or /opt/homebrew/bin/ - we can sort this out during the course. 

Note: Another option to install the compiler is to use MacPorts (ports.macports.org/port/gcc11) but we haven't tested that this works yet.

##### Using a compiler with automated compilation in VS Code (optional) 

Finally, you can tell Visual Studio Code to use it if you're using that as an IDE (this is not necessary, you can and maybe should always use the terminal!)

You should then open VS Code and go to Settings, which is the wheel on the bottom of the window  (this was found as File->Preferences->Settings in older versions), The main window of VS Code will turn into a list of settings. 

In the top bar, search for "compiler" and you should see  C_Cpp › Default: Compiler Path.  Put in:

```
[your installation path from brew]/g++-13
```

Then write a simple code in the editor window, e.g. the one below: 

```
// L1/simple.cpp
// Another particularly simple example of C++ in action!
// Niels Walet, last updated 22/01/2023
#include <iostream>

int main()
{
const int current_year = 2023;
std::cout << "C++ is the best programming language in "<<current_year<<"!"<< std::endl;
return 0;
}
```

Then, try to compile it (this is called a "build task" in Visual Studio). 

What a build task does is calling the compiler with some flags (you could also do the same in the terminal window yourself).  
By default, you will have clang installed or mac's version of g++ (which is basically clang so it's not good) and Visual Studio will use that. 

But if your installation of gcc/g++11 or gcc12 went well, you should see g++11 or 12 in the drop-down menu. You should also be able to choose g++11 as the option if you are starting Visual Studio for the first time. 

### Linux 

The installation of the compiler and text editor of your choice will depend on the Linux distribution you have - feel free to fork this repository and make a pull request for your configuration as it will help others! 

Also, vim is better than emacs. Fight me. 

### Windows

#### Installing a compiler

We suggest to install the latest gcc compilers using mingw. Simple instructions on how to do this are 
<[at this link](https://code.visualstudio.com/docs/cpp/config-mingw#_installing-the-mingww64-toolchain)>

#### Installing a text editor

You can use any text editor you'd like, and we suggest an Integrated Development Environment (IDE) like Visual Studio Code. You don't need to use all the features (e.g. automatic compilation etc...) and we will not necessarily do so in the course, but this provides a terminal as well where you can enter your commands as well as the text editor. 

You can download and install Visual Studio Code from <[here](https://code.visualstudio.com/docs/setup/windows)>. This website also has instructions on how to set up and configure the IDE to work with the gcc compiler above.

## Instructions for lxplus (WIP)

If you have an lxplus account, all you need to do is to set up a recent compiler, and you should be all set to start! This is generally done for you in the most recent lxplus nodes (lxplus9) but you can also choose your the compiler from one of the most recent <[LCG releases](https://lcginfo.cern.ch)>. 

## Instructions for using lab computers (coming soon) 

## Troubleshooting

### Mac 

If you have an error like this on the hello world program:

```
/usr/local/Cellar/gcc/13.1.0/bin/g++-13 --std=c++20 -c -g -Wall -Wextra -o hello.o hello.cpp
In file included from /usr/local/Cellar/gcc/13.1.0/include/c++/13/bits/postypes.h:40,
                 from /usr/local/Cellar/gcc/13.1.0/include/c++/13/iosfwd:42,
                 from /usr/local/Cellar/gcc/13.1.0/include/c++/13/ios:40,
                 from /usr/local/Cellar/gcc/13.1.0/include/c++/13/ostream:40,
                 from /usr/local/Cellar/gcc/13.1.0/include/c++/13/iostream:41,
                 from hello.cpp:3:
/usr/local/Cellar/gcc/13.1.0/include/c++/13/cwchar:44:10: fatal error: wchar.h: No such file or directory
   44 | #include <wchar.h>
      |          ^~~~~~~~~
compilation terminated.
```
it means that your Command Line Tools are too old, and you need to uninstall/reinstall as above. This will usually take 10-15' on a recent mac. 
