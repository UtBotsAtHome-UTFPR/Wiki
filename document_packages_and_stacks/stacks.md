# stack_name

**A stack documentation must start with description of the packages domain and a list of all packages:**

This stack contains `<domain>` related packages, such as:
- package_a
- package_b
- package_c

**If any of its packages uses custom messages, services or actions, add the following:**

And is dependant on:

- [utbots_dependencies](https://github.com/UtBotsAtHome-UTFPR/utbots_dependencies)


## Installation

**You should add instructions on how to install the stack. `--recurse-submodules` is necessary when the stack contains submodules (linked subrepositories):**
```bash
cd ~/catkin_ws/src
git clone --recurse-submodules <stack_url>.git
```

**If any of its packages uses custom messages, services or actions, add the following:**
```bash
cd ~/catkin_ws/src
git clone https://github.com/UtBotsAtHome-UTFPR/utbots_dependencies.git
```
### Dependencies

**You can create a bash file or another method for automatically installing each package dependencies and explain its usage.**

**If not, you should add the following:**

See the dependencies installation procedure for each package accessing its README.md file or below, in [Packages Description](#packages-description).

### Building

**Instructions on how to build the package are a good practice**:

```bash
cd ~/catkin_ws
catkin_make -DCMAKE_BUILD_TYPE=Release
```

## Running

**If the usage is complex and the stack contains several packages, you might want to add the following:**

See the usage explanation accessing each package in the repository (or the overview below)

**In this case, adding functionality diagrams might be a good alternative. Otherwise, you can write briefly the usage for the stack's packages**

## Packages Description

**Adding an overview for a package is only encouraged when the package is not original and you cannot edit its README.md file according to the `packaged.md` guide. In this case, you can document it in this section. For instance:**

### Non-original package (example)
- Some information
- Another information

#### Installation
Instructions for installation

#### Running
Instructions for usage
