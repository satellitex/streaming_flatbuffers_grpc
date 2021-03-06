cmake_minimum_required(VERSION 2.8)
PROJECT(faltest C CXX)

SET(CMAKE_CXX_FLAGS "-std=c++1y -Wall -fPIC")
SET(CMAKE_CXX_FLAGS_RELEASE "-O3")
SET(CMAKE_CXX_FLAGS_DEBUG   "-g -Wextra -Wno-unused-parameter -O0")
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules)

option(BENCHMARKING "Build benchmarks" OFF)
option(TESTING "Build tests" ON)

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug)
endif()
message(STATUS "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}")
message(STATUS "-DTESTING=${TESTING}")
message(STATUS "-DBENCHMARKING=${BENCHMARKING}")

set(IROHA_SCHEMA_DIR "${PROJECT_SOURCE_DIR}/schema")

include_directories(
)

#include("cmake/dependencies.cmake")
#add_subdirectory(schema)

link_directories(${PROJECT_BINARY_DIR}/lib)

if(TESTING)
    enable_testing()
##    add_subdirectory(test)
endif()


if(BENCHMARKING)
    add_subdirectory(benchmark)
endif()
