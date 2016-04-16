cmake_minimum_required(VERSION 3.5.1)

project(untransformer)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra -Wconversion -Werror -pedantic")

if (NOT CMAKE_BUILD_TYPE)
    message("The CMAKE_BUILD_TYPE variable is not set. Setting to release...")
    set(CMAKE_BUILD_TYPE Release)
endif ()

message(STATUS "Build type: ${CMAKE_BUILD_TYPE}")

if (CMAKE_BUILD_TYPE MATCHES Debug)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0")
    set(CMAKE_VERBOSE_MAKEFILE TRUE)
else ()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")
endif ()

add_executable(${PROJECT_NAME} main.cpp)

find_package(Threads)
target_link_libraries (${PROJECT_NAME} ${CMAKE_THREAD_LIBS_INIT})
