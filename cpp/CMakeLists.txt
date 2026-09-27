cmake_minimum_required(VERSION 3.16)

project(
    robocon_vision_cpp
    VERSION 1.0.0
    DESCRIPTION "ROBOCON Vision Assignment 1 - C++ Otsu/Canny video task"
    LANGUAGES CXX
)

# The task requires C++17; it is declared in README.md and in cpp/README.md.
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Default to a release-style build when no build type was given
# (single-config generators such as "Unix Makefiles" / "Ninja").
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
    set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
endif()

# OpenCV: only the modules that main.cpp / transform.cpp actually use.
find_package(OpenCV REQUIRED COMPONENTS core imgproc videoio)

# Eigen3: header-only requirement (>= 3.3). Eigen3Config.cmake ships with
# libeigen3-dev on Ubuntu, so the imported Eigen3::Eigen target is available.
find_package(Eigen3 3.3 REQUIRED NO_MODULE)

add_executable(
    cpp_task
    src/main.cpp
    src/transform.cpp
)

# "include/" is where transform.hpp lives; the sources include it as
# #include "transform.hpp", not as a relative path.
target_include_directories(
    cpp_task
    PRIVATE
        "${CMAKE_CURRENT_SOURCE_DIR}/include"
        ${OpenCV_INCLUDE_DIRS}
)

target_link_libraries(
    cpp_task
    PRIVATE
        ${OpenCV_LIBS}
        Eigen3::Eigen
)

# Helpful when the compiler needs to be told that OpenCV/Eigen are system
# packages that the student installed deliberately.
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(cpp_task PRIVATE -Wall -Wextra)
endif()

message(STATUS "OpenCV version : ${OpenCV_VERSION}")
message(STATUS "OpenCV include : ${OpenCV_INCLUDE_DIRS}")
message(STATUS "Eigen3 version : ${Eigen3_VERSION}")
message(STATUS "C++ standard   : ${CMAKE_CXX_STANDARD}")
