cmake_minimum_required(VERSION 3.0.0)
project(cpp-example VERSION 0.1.0)

include_directories(.)

include(CTest)
enable_testing()

add_executable(cpp-example main.cpp network.c nl.c)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
