cmake_minimum_required(VERSION 3.0.0)

project(openGL_mini VERSION 0.1 LANGUAGES CXX)

# The version number.
set (openGL_mini_VERSION_MAJOR 0)
set (openGL_mini_VERSION_MINOR 1)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)


find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIR})
set (EXTRA_LIBS ${EXTRA_LIBS} ${OPENGL_LIBRARIES})
set(EXTRA_LIBS ${EXTRA_LIBS} glfw)
set(EXTRA_LIBS ${EXTRA_LIBS} GLEW)


foreach(lib ${EXTRA_LIBS})
    message("Including: " ${lib})
    endforeach(lib)

include_directories(src/)
set( project_sources
   main.cpp
   #src/noise_filter.cpp
   #src/segmentation.cpp
   #src/pixattr.cpp
)

add_executable(${PROJECT_NAME} ${project_sources})
target_link_libraries (${PROJECT_NAME}  ${EXTRA_LIBS})

# add_custom_command(
#         TARGET openGL_mini POST_BUILD
#         COMMAND ${CMAKE_COMMAND} -E copy
#                 ${CMAKE_SOURCE_DIR}/test.png
#                 ${CMAKE_CURRENT_BINARY_DIR}/test.png)

