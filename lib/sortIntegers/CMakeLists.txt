message("-----in lib/sortIntegers")

#[=[
To build the library, create a CMakeLists.txt file in lib/sortIntegers/ that builds a library called sortIntegers using the add_library command. We also need to declare the location of public interface headers that will be included by clients of the library. This can be done using the target_include_directories command to specify PUBLIC headers in the include directory with $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>. This last complex generator expression sets the include path to use when building the project. To determine the path at install time, we can also add $<INSTALL_INTERFACE:include>. The first portion of the generator expression is a condition determining when it applies, and the latter portion is the path.
]=]

add_library(sortIntegers SortIntegers.cpp)

target_include_directories(sortIntegers PRIVATE  
  $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/include>)

set_target_properties(sortIntegers PROPERTIES CXX_STANDARD 17)
target_compile_features(sortIntegers PRIVATE cxx_std_11)


#target_include_directories(sortIntegers PRIVATE )


cmake_print_variables(CMAKE_CURRENT_BINARY_DIR)

#[=[
One way to debug the value of a generator expression is to use the file(GENERATE) command, which is covered in Section 21.3, “Reading And Writing Files Directly”. The generator expression can be written to a temporary file and inspected when CMake finishes execution.
]=]

set(incDirs $<TARGET_PROPERTY:sortIntegers,INCLUDE_DIRECTORIES>)
  set(genex "-I$<JOIN:${incDirs}, -I>")
  file(GENERATE OUTPUT genex.txt CONTENT "${genex}\n")
