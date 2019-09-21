cmake_minimum_required(VERSION 3.14)
project(LibLZMA)

set(CMAKE_CXX_STANDARD 14)

add_library(${PROJECT_NAME} mylib.cpp include/mylib.hpp)

target_include_directories(${PROJECT_NAME} PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>)

install(TARGETS LibLZMA
        EXPORT mylib-targets
        PUBLIC_HEADER DESTINATION include
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib
        RUNTIME DESTINATION bin)

install(EXPORT mylib-targets
NAMESPACE LibLZMA::
FILE mylib-config.cmake
DESTINATION lib/cmake/mylib)