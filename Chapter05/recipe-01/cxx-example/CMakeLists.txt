cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

project(recipe-01 CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_custom_target(unpack-eigen
  ALL
  COMMAND
    ${CMAKE_COMMAND} -E tar xzf ${PROJECT_SOURCE_DIR}/eigen-eigen-5a0156e40feb.tar.gz
  COMMAND
    ${CMAKE_COMMAND} -E rename eigen-eigen-5a0156e40feb eigen-3.3.4
  WORKING_DIRECTORY
    ${PROJECT_BINARY_DIR}
  COMMENT
    "Unpacking Eigen3 in ${PROJECT_BINARY_DIR}/eigen-3.3.4"
  )

add_executable(linear-algebra linear-algebra.cpp)
add_dependencies(linear-algebra unpack-eigen)
target_include_directories(linear-algebra
  PRIVATE
    ${PROJECT_BINARY_DIR}/eigen-3.3.4
  )
