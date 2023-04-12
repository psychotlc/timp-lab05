cmake_minimum_required(VERSION 3.0)

project(banking_test)

set (BUILD_TESTS ON)

set (PROJECT_NAME banking)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/${PROJECT_NAME})

if(BUILD_TESTS)
  enable_testing()
  add_executable(check ${CMAKE_CURRENT_SOURCE_DIR}/tests/test.cpp)
  target_include_directories(check PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/banking)
  target_link_libraries(check banking gtest_main gtest)
  add_test(NAME check COMMAND check)
endif()