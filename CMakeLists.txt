# top level CMakeLists

cmake_minimum_required(VERSION 3.13)

set(VERBOSE True)

project(codeblocks VERSION 0.1)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

configure_file("src/include/config.h.in" "src/include/config.h")

set(CMAKE_POSITION_INDEPENDENT_CODE ON)

add_subdirectory(src)
