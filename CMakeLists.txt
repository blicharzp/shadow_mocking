cmake_minimum_required (VERSION 3.10)
project(Foo)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_FLAGS "-Wall -pedantic")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(DUPA "RELEASE" CACHE STRING "Build type")

if(DUPA STREQUAL "RELEASE")
    set(SOURCES foo_production.cpp)
elseif(DUPA STREQUAL "TEST")
    set(SOURCES foo_test.cpp)
else()
    message(FATAL_ERROR "Please provide build type.")
endif()

add_executable(main main.cpp ${SOURCES})

target_include_directories(main PRIVATE .)

set(DUPA "RELEASE" CACHE STRING "Build type" FORCE)