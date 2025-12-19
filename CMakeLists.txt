cmake_minimum_required(VERSION 3.27)
project(GLExperiments)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(glfw3 REQUIRED)



add_executable(window "${CMAKE_CURRENT_SOURCE_DIR}/makingawindow.cpp" "${CMAKE_CURRENT_SOURCE_DIR}/Libs/glad.c")
target_include_directories(window PUBLIC "${CMAKE_CURRENT_BINARY_DIR}/Includes")
target_link_directories(window PUBLIC "${CMAKE_CURRENT_BINARY_DIR}/Libs")

target_link_libraries(window 
    glfw 
    "-framework OpenGL" 
    "-framework Cocoa" 
    "-framework IOKit" 
    "-framework CoreVideo"
)

file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/required/" 
     DESTINATION "${CMAKE_BINARY_DIR}/bin/")