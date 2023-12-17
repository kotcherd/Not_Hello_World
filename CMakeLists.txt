cmake_minimum_required(VERSION 3.23)

project(deet C CXX)

include(CMakePrintHelpers)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/bin")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/lib")

add_subdirectory(lib)
add_subdirectory(tools)


