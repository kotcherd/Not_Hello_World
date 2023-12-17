message("-----in tools/fibsorter")

#[=[
Similarly, create a CMakeLists.txt file in tools/fibSorter/ that builds a program called fibSorter using the add_executable command along with the target_link_libraries command. Notice that the location of the include directories for the library are automatically propagated to the fibSorter that uses it. This means you could change where the include directories for the library are, and the fibSorter build process would not need to be modified. If you happen to test that out, make sure to change the file paths back, as they will be checked.
]=]

cmake_print_variables(INCLUDE_DIRECTORIES)

add_executable(fibSorter main.cpp)

set_target_properties(fibSorter PROPERTIES CXX_STANDARD 17)
target_compile_features(fibSorter PRIVATE cxx_std_11)

target_link_libraries(fibSorter PUBLIC sortIntegers)
include_directories("${CMAKE_SOURCE_DIR}/lib/sortIntegers/include")
