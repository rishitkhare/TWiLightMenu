cmake_minimum_required(VERSION 3.20)
project(twilight_intel)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(SYSTEM "${CMAKE_CURRENT_SOURCE_DIR}/ndsincludes")
include_directories(SYSTEM "${CMAKE_CURRENT_SOURCE_DIR}/universal/include")
include_directories(SYSTEM "${CMAKE_CURRENT_SOURCE_DIR}/universal/arm7/include")
include_directories(SYSTEM "${CMAKE_CURRENT_SOURCE_DIR}/universal/arm9/include")
include_directories(SYSTEM "${CMAKE_CURRENT_SOURCE_DIR}/romsel_dsimenutheme/arm9/include")


# Essential DS defines to 'un-gray' the code in headers
add_definitions(-D__NDS__ -DARM9)

# Recursively finds all code in booter, common, settings, etc.
file(GLOB_RECURSE ALL_SOURCES
        "${CMAKE_CURRENT_SOURCE_DIR}/*.c"
        "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
        "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)

# Dummy target to trigger indexing
add_executable(twilight_dummy ${ALL_SOURCES})
