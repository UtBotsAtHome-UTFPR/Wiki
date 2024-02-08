# Migrating ROS Noetic Packages to ROS Humble

This document is meant to be used as a guide for transcripting existing packages from ROS Noetic to ROS2 Humble

## Create a Package

Firstly, it is advisable to [create a package](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html) in ros humble. For now it will be left empty

It is important to use CMake for C++ and python for python code.

## Migration Process C++

The official guide on how to do this is presented at [this link](https://docs.ros.org/en/humble/How-To-Guides/Migrating-from-ROS1/Migrating-CPP-Packages.html)

### CMakeLists.txt file

The minimum version of cmake is now VERSION 3.5.

For compatibility reasons it is advisable to add the following lines after the call of `project(name)`.

```xml
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()
```

The move from catkin to the new ament_cmake system induced many changes. Firslty, find package calls only allow a single component per call, which means

```xml
find_package(catkin REQUIRED COMPONENTS
gazebo_ros
p3dx_control
p3dx_description
)
```

will be converted to 

```xml
find_package(ament_cmake REQUIRED)

find_package(gazebo_ros REQUIRED)

find_package(p3dx_control REQUIRED)

find_package(p3dx_description REQUIRED)
```

As you can see, catkin package was substituted to ament_cmake, this is a necessary step.

The `catkin_package()` call must be moved to the end of the file and replace by `ament_package()`. 

Other arguments covered by functions have changed names and MUST be called before `ament_packages`. `CATKIN_DEPENDS` -> `ament_export_dependencies`, `INCLUDE_DIRS` -> `ament_export_include_directories()`. (THIS DOES NOT INCLUDE THE FUNCTION `INCLUDE_DIRECTORIES`). Additional information on such functions can be found in IF YOU SEE THIS UPDATE IT OR TELL DAVID SEGALLE TO UPDATE IT, ROS DOC WEBSITE IS CURRENTLY NOT ON AIR.LINKS FOR FUNCTIONS FOR ROS 1 AND ROS 2 MUST BE ADDED

The call of `add_executable()` should be moved to after `find_package()` or any of the `CATKIN_DEPENDS` and `INCLUDE_DIRS` like functions .


`target_link_libraries()` should be moved to immediately after `add_executables()`. it's name changed to `ament_target_dependencies()`. This new function automatically handles include directories defined in `INCLUDE_DIRS` as well as linking libraries defined in `_LIBRARIES`. However, other targets must be manually set.

```xml
target_link_libraries(mover ${catkin_LIBRARIES})
```
Now becomes

```xml
ament_target_dependencies(mover
  rclcpp
  std_msgs
  controller_manager
  geometry_msgs)
```

mover is the name of the executable in this case.

```xml
install(TARGETS mover
  DESTINATION lib/${PROJECT_NAME})
```

To be honest I have no idea what it does, however, something similar is probably present at the end of your file. You can move it up as long as it's after `ament_target_dependencies`

If your project contains launch files the following must be added in order for the compiler to find them:

```xml
install(DIRECTORY launch
DESTINATION share/${PROJECT_NAME})
```

For the cases where the user might want to access included directories in downstream packages:

```xml
install(DIRECTORY include/
  DESTINATION include)

ament_export_include_directories(include)
ament_export_dependencies(std_msgs)
```
And lastly, as mentioned previously, The last thing in the file should be a call to `ament_package`

### The Source Code

The ros C++ API is now named rclcpp, so the include went from `#include "ros/ros.h"` to `#include "rclcpp/rclcpp.hpp"`

included messages, services and actions now have /msg/, /srv/ and /action respectively. Messages are now separated by underscore and lastly, tags have been updated to .hpp. Essentially `#include <geometry_msgs/PointStamped.H>` now becomes `#include <geometry_msgs/msg/point_stamped.hpp`.

Variable declaration of message types also have ::msg:: added to them.
