cmake_minimum_required(VERSION 2.8.12)
project(test_package CXX)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

option(TEST_SHARED_LIB "Use package in a shared library")
if(TEST_AS_SHARED_LIB)
  add_library(${PROJECT_NAME}2 SHARED test_package.cpp)
  target_link_libraries(${PROJECT_NAME}2 ${CONAN_LIBS})
  target_include_directories(${PROJECT_NAME}2 PRIVATE ${CONAN_INCLUDE_DIRS})
  set_property(TARGET ${PROJECT_NAME}2 PROPERTY CXX_STANDARD 17)
endif()

# if(MSVC)
#   add_definitions(-DLIBRARY_EXPORTS)
# endif()

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})
target_include_directories(${PROJECT_NAME} PRIVATE ${CONAN_INCLUDE_DIRS})
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 17)
