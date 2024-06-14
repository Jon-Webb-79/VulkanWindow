========================
GLFW X11 Build Example
========================

This repository provides an example of how to set up and build GLFW for X11 on 
Wayland platforms. The code ensures that GLFW is correctly configured to use 
X11, which is necessary for properly rendering the window title bar and icons 
on some Wayland systems.  In this instance we are using Vulkan to provide 
functionality within the window

Project Structure
==================
The project has the following structure:

.. code-block:: none

    .
    ├── data
    ├── VulkanWindow
    │   ├── build
    │   ├── CMakeLists.txt
    │   ├── glfw
    │   │   ├── ... (GLFW source files)
    │   ├── include
    │   ├── main.cpp
    │   └── test
    │       ├── CMakeLists.txt
    │       └── test.cpp
    ├── LICENSE
    ├── README.rst
    └── scripts
        ├── bash
        │   ├── build.sh
        │   ├── compile.sh
        └── zsh
            ├── build.zsh
            ├── compile.zsh

Setup and Build Instructions
============================
To build and run the project, follow these steps:

1. **Clone the Repository**:

    .. code-block:: bash

        git clone https://github.com/Jon-Webb-79/VulkanWindow.git
        cd VulkanWindow/VulkanWindow

2. **Create a Build Directory and Run CMake**:

    .. code-block:: bash

        mkdir -p build
        cd build
        cmake ..

3. Change the CMakeLists.txt file to implement the CMake version loaded on
   your computer.

4. **Build the Project**:

    .. code-block:: bash

        make

5. **Run the Executable stored in VulkanWindow/build/**:

    .. code-block:: bash

        ./VulkanWindow

Pre-Written Scripts
===================
The repository includes pre-written scripts for building and compiling the code. 
These scripts are located in the `scripts/zsh` and `scripts/bash` directories.

**Zsh Scripts**:
-----------------
- `build.zsh`: Script to configure and build the project using zsh.
- `compile.zsh`: Script to compile the project using zsh.

**Bash Scripts**:
------------------
- `build.sh`: Script to configure and build the project using bash.
- `compile.sh`: Script to compile the project using bash.

Usage:
------

**Zsh**:

.. code-block:: zsh

    # To build the project
    ./scripts/zsh/build.zsh

    # To compile the project
    ./scripts/zsh/compile.zsh

**Bash**:

.. code-block:: bash

    # To build the project
    ./scripts/bash/build.sh

    # To compile the project
    ./scripts/bash/compile.sh

Purpose
=======
This project serves as an example for setting up and building GLFW with X11 
support on Wayland platforms. By following the instructions provided, users 
can ensure that GLFW is correctly configured to render window title bars and 
icons, which may not be displayed correctly when using Wayland.

Contributing
============
Contributions are welcome! If you have any suggestions or improvements, 
feel free to create a pull request or open an issue.

License
=======
This project is licensed under the MIT License. See the `LICENSE` file for details.
