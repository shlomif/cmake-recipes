# set minimum cmake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# project name
project(recipe-06)

# define tests
enable_testing()

add_test(example ${PROJECT_SOURCE_DIR}/test.sh)

# we expect this test to fail
set_tests_properties(example PROPERTIES WILL_FAIL true)
