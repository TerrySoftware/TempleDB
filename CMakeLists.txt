cmake_minimum_required(VERSION 3.10)
project(tdb)

file(GLOB C_SOURCE_CODE "src/*.c")
file(GLOB CPP_SOURCE_CODE "src/*.cpp")

set(CMAKE_BUILD_TYPE Debug)

add_executable(${PROJECT_NAME} ${C_SOURCE_CODE} ${CPP_SOURCE_CODE})

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(${PROJECT_NAME} PRIVATE -fsanitize=address -fno-omit-frame-pointer)
    target_link_options(${PROJECT_NAME} PRIVATE -fsanitize=address)
endif()

target_include_directories(${PROJECT_NAME} PRIVATE include)


