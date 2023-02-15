set(CMAKE_VERBOSE_MAKEFILE TRUE)
cmake_minimum_required(VERSION 3.25.1)
project(opengl_matsuzaki_sigeru CXX)
add_executable(${PROJECT_NAME} src/main.cpp)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Werror)


include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/58d77fa8070e8cec2dc1ed015d66b454c8d78850.zip
)
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)
enable_testing()
add_executable(${PROJECT_NAME}-googletest test/main.cpp)
target_link_libraries(${PROJECT_NAME}-googletest GTest::gtest_main)
include(GoogleTest)