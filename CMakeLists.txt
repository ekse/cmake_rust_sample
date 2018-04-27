cmake_minimum_required(VERSION 3.0)

project(CMakeRustSample)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

enable_language(Rust)
include(CMakeCargo)

include_directories("include")
add_subdirectory(test-lib)

add_executable(helloworld main.cpp)

if(WIN32)
    target_link_libraries(helloworld test-lib ws2_32 userenv)
else()
    target_link_libraries(helloworld test-lib dl pthread)
endif()

