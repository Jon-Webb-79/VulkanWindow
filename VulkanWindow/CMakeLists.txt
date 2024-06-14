# ================================================================================
# ================================================================================
# - File:    CMakeLists.txt
# - Purpose: Primary CMake file for C build system
#
# Source Metadata
# - Author:  Jonathan A. Webb
# - Date:    June 13, 2024
# - Version: 1.0
# - Copyright: Copyright 2024, Jonathan A. Webb Inc.
# ================================================================================
# ================================================================================
cmake_minimum_required(VERSION 3.29.5)
project(VulkanWindow)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set compiler flags
if (CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -Wpedantic")
endif()

# Include ExternalProject module to manage external dependencies
include(ExternalProject)

# Define GLFW as an external project
ExternalProject_Add(
    glfw
    GIT_REPOSITORY https://github.com/glfw/glfw.git
    GIT_TAG latest
    CMAKE_ARGS -DGLFW_BUILD_EXAMPLES=OFF
               -DGLFW_BUILD_TESTS=OFF
               -DGLFW_BUILD_DOCS=OFF
               -DGLFW_BUILD_INSTALL=OFF
               -DGLFW_BUILD_WAYLAND=OFF
               -DGLFW_BUILD_X11=ON
    PREFIX ${CMAKE_BINARY_DIR}/glfw
    INSTALL_COMMAND ""
)

# Find the Vulkan package
find_package(Vulkan REQUIRED)

# Define the executable
add_executable(VulkanWindow main.cpp)

# Include GLFW and Vulkan directories
ExternalProject_Get_Property(glfw source_dir binary_dir)
target_include_directories(VulkanWindow PRIVATE ${source_dir}/include)
target_include_directories(VulkanWindow PRIVATE ${Vulkan_INCLUDE_DIRS})

# Link the GLFW and Vulkan libraries
add_dependencies(VulkanWindow glfw)
target_link_libraries(VulkanWindow PRIVATE ${binary_dir}/src/libglfw3.a Vulkan::Vulkan)

# Set the output directory for the executable
set_target_properties(VulkanWindow PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}
)

# ================================================================================
# ================================================================================
# eof
