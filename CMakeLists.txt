cmake_minimum_required(VERSION 3.0)

project(CMakeRustSample)

set(CMAKE_LOCAL_ROOT ${CMAKE_SOURCE_DIR}/cmake)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_LOCAL_ROOT}/Modules")

enable_language(Rust)
include(CMakeCargo)

include_directories("include")
add_subdirectory(test-lib)

add_executable(helloworld main.cpp)
target_link_libraries(helloworld test-lib ws2_32 userenv)


