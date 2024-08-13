# package_name
- Give an overview of the package functionalities and description in topics
- You should describe the tool you are implementing in ROS, if it is the case
- You should also give a brief explanation of the functionalities you implemented in it
- Your package documentation must contain an Installation section, then an Usage section. You may add new subsections inside these sections and add new ones after them
- The following subsections and text are an example

## Installation

### Building

**This subsection is not necessary always. If the package is defined outside a stack, you should add instruction on how to build it:**
```
cd ~/catkin_ws/src
git clone <repo_url>.git
cd ..
catkin_make
```

### Dependencies

**If the package uses actions or custom messages, it must have the following in the Dependencies section:**

This package must be used alongside the [utbots_dependencies](https://github.com/UtBotsAtHome-UTFPR/utbots_dependencies) as it uses some of the message and action definitions. You can do this with:

```bash
cd ~/catkin_ws/src/
git clone https://github.com/UtBotsAtHome-UTFPR/utbots_dependencies.git
cd ..
catkin_make
```

**You should provide the full description of the installation of the dependencies. For instance, with Python, you may specify the Python version and write the following for installing requirements:**

The code runs on Python 3.8.

```bash
roscd <package_name>
pip install -r requirements.txt
```

**OBS:** You may write relevant observations

## Running
**You should detail how to run the nodes and scripts in the package. For instance:**

First, initialize ROS (if not already):
```bash
roscore
```
Then, run the node:
```bash
rosrun <package_name> <node_name>
```

**You should also add usage examples for another important control commands and features. You can add new subsections for that also. Such as:**

### Enable control (example)

Enable the node processing with:

```bash
rosservice call \enable
```

## New sections (example)
**You may add new sections in order to describe, for example, the nodes of a package or a specific functionality of the package**