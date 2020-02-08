cmake_minimum_required(VERSION 2.8.12)
project(cmake_wrapper)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

if(MSVC)
  add_definitions(-DLIBRARY_EXPORTS)
endif()
add_subdirectory("source_subfolder")
