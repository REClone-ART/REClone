
cmake_minimum_required(VERSION 3.20)

project(REClone
    VERSION 0.1.0
    DESCRIPTION "Independent RE Engine-inspired format, asset and runtime ecosystem"
    LANGUAGES CXX
)

# C++ configuration
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Build options
option(RECLONE_BUILD_CLI "Build REClone command-line tools" ON)
option(RECLONE_BUILD_EDITOR "Build REClone desktop editor" OFF)
option(RECLONE_BUILD_RUNTIME "Build REClone runtime" OFF)
option(RECLONE_BUILD_TESTS "Build REClone tests" OFF)

# Compiler warnings
if(MSVC)
    add_compile_options(/W4 /permissive-)
else()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Project modules will be added as they are implemented.
# The CLI target will be added in a later step.

message(STATUS "-----------------------------------")
message(STATUS "REClone ${PROJECT_VERSION}")
message(STATUS "C++ standard: ${CMAKE_CXX_STANDARD}")
message(STATUS "CLI: ${RECLONE_BUILD_CLI}")
message(STATUS "Editor: ${RECLONE_BUILD_EDITOR}")
message(STATUS "Runtime: ${RECLONE_BUILD_RUNTIME}")
message(STATUS "Tests: ${RECLONE_BUILD_TESTS}")
message(STATUS "-----------------------------------")
