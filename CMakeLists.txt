
cmake_minimum_required(VERSION 3.20)

project(REClone
    VERSION 0.1.0
    DESCRIPTION "An independent engine and tooling project inspired by RE Engine research"
    LANGUAGES CXX
)

# Require C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Export compile commands for IDEs and development tools
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Project configuration
option(RECLONE_BUILD_TESTS "Build REClone tests" OFF)
option(RECLONE_BUILD_TOOLS "Build REClone development tools" OFF)

# Shared compiler warnings
if(MSVC)
    add_compile_options(/W4 /permissive-)
else()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Future project modules will be added here:
#
# add_subdirectory(src/core)
# add_subdirectory(src/serialization)
# add_subdirectory(src/assets)
#
# Development tools:
# add_subdirectory(tools)
#
# Automated tests:
# if(RECLONE_BUILD_TESTS)
#     enable_testing()
#     add_subdirectory(tests)
# endif()

message(STATUS "Configuring REClone ${PROJECT_VERSION}")
message(STATUS "C++ standard: ${CMAKE_CXX_STANDARD}")
message(STATUS "Build tests: ${RECLONE_BUILD_TESTS}")
message(STATUS "Build tools: ${RECLONE_BUILD_TOOLS}")
message(STATUS "REClone foundation configured successfully.")
