cmake_minimum_required(VERSION 3.27)
project(GLExperiments)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/)

find_package(glad CONFIG REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)



add_executable(window "${CMAKE_CURRENT_SOURCE_DIR}/makingawindow.cpp")
target_include_directories(window PRIVATE
    "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_link_libraries(window 
    glfw
    glad::glad
    GLUT::GLUT
    glm::glm
    OpenGL::GL
)

file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/assets" 
    DESTINATION "${CMAKE_BINARY_DIR}/bin/")
file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/shaders"
    DESTINATION "${CMAKE_BINARY_DIR}/bin")