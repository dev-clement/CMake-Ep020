cmake_minimum_required(VERSION 3.20)

project(CustomTarget
        VERSION 0.0.1
        DESCRIPTION "A leading rooster app"
        LANGUAGES CXX)


set(TARGET_NAME Rooster)
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(${TARGET_NAME} ${CMAKE_SOURCE_DIR}/main.cpp ${CMAKE_SOURCE_DIR}/person/src/person.cpp)
target_include_directories(${TARGET_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/person/include)
target_include_directories(${TARGET_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/include)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")
include(ClangFormat)
add_clang_format_target(format-code ${PROJECT_SOURCE_DIR})
add_dependencies(${TARGET_NAME} format-code)