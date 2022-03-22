cmake_minimum_required(VERSION 3.8)
project(nmp)

set(SOURCE main.cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Adding googletest to project
option(PACKAGE_TESTS "Build the tests" ON)
if(PACKAGE_TESTS)
    enable_testing()
    include(GoogleTest)
    add_subdirectory(tests)
endif()

# # example: package_add_test(test1 test1.cpp)
# macro(package_add_test TESTNAME)
#     # create an executable in which the tests will be stored
#     add_executable(${TESTNAME} ${ARGN})
#     # link the Google test infrastructure, mocking library, and a default main function to
#     # the test executable.  Remove g_test_main if writing your own main function.
#     target_link_libraries(${TESTNAME} gtest gmock gtest_main)
#     # gtest_discover_tests replaces gtest_add_tests,
#     # see https://cmake.org/cmake/help/v3.10/module/GoogleTest.html for more options to pass to it
#     gtest_discover_tests(${TESTNAME}
#         # set a working directory so your project root so that you can find test data via paths relative to the project root
#         WORKING_DIRECTORY ${PROJECT_DIR}
#         PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "${PROJECT_DIR}"
#     )
#     set_target_properties(${TESTNAME} PROPERTIES FOLDER tests)
# endmacro()

