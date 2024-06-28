# Qt6 plugin for the CLX000 CAN logger/interface
This project contains source code for a [Qt6 Serial Bus](https://doc.qt.io/qt-6/qtserialbus-index.html) module plugin. The purpose is to allow the CLX000 CAN bus data logger & interface from CSS Electronics to stream data into applications utilizing the Qt6 Serial Bus framework (e.g. [SavvyCAN](https://github.com/collin80/SavvyCAN)).

----

## Building
If not targeting a system-wide Qt installation, the `vcpkg` (integrated as a git submodule) can be utilized. Current configuration is only enabled for [CMake](https://cmake.org/).

### Building with vcpkg
Download the code to your development environment. Note that `--recursive` will include the submodule files.

```
git clone --recursive https://github.com/douglasheld2/clx000-qt6-plugin.git
cd clx000-qt6-plugin
```

Next, bootstrap the [vcpkg](https://github.com/microsoft/vcpkg) installation in the submodule.

```
./vcpkg/bootstrap-vcpkg.sh
```

Create a folder for out-of-tree building, and configure cmake.

```
mkdir build
cd build
cmake -DCMAKE_TOOLCHAIN_FILE=../vcpkg/scripts/buildsystems/vcpkg.cmake ..
```

During configuration, all required dependencies should be downloaded, built and installed locally in the `vcpkg` folder. After configuration, build the plugin with

```
cmake --build .. --target clx000canbus
```

----

## Installation

### System-wide usage
Copy the module to the system Qt6 installation into the `plugins/canbus` directory. For example, `cp clx000canbus.so Qt/6.7.2/gcc_64/plugins/canbus/ `

### Application local usage.
Copy the module to the application's plugin directory, with similar directory structure. For example, `cp clx000canbus.dylib Applications/SavvyCAN.app/Contents/PlugIns/canbus/ `. The `canbus` directory may first need to be created.
Note, The application must have been built with the local path for loading modules.

----
## About the CLX000

For details on using the CLX000 as a CAN bus data logger and CAN interface, see the products pages and documentation:
- [CL1000](https://www.csselectronics.com/screen/product/can-bus-logger-canlogger1000)
- [CL2000](https://www.csselectronics.com/screen/product/can-bus-logger-canlogger2000)
- [Docs](https://www.csselectronics.com/screen/page/can-logger-resources#clx000-resources)

----

## Contribution & support
Feature suggestions, pull requests or questions are welcome!

You can contact us at CSS Electronics below:
- [www.csselectronics.com](https://www.csselectronics.com)
- [Contact form](https://www.csselectronics.com/screen/page/can-bus-logger-contact)  
