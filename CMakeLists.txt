cmake_minimum_required(VERSION 3.7)
project(OpenGLSetup)

set(CMAKE_CXX_STANDARD 11)

set(HELLO_TEXTURES_FILES hello_textures.cpp GLAD/src/glad.c)
set(HELLO_TEXTURES_FILES_4_5 hello_textures_4.5.cpp GLAD/src/glad.c)
set(HELLO_TRIANGLE_FILES hello_triangle.cpp GLAD/src/glad.c)
set(HELLO_SHADERS_FILES hello_shaders.cpp GLAD/src/glad.c)

set(HEADER_FILES shader.h)

set(dir ${CMAKE_CURRENT_SOURCE_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${dir}/build)

include_directories(include)

#Include library files
include_directories(GLAD/include)
include_directories(glm/include)

file(COPY resources DESTINATION ${dir}/build)
file(COPY shaders DESTINATION ${dir}/build)


#Add deps
add_subdirectory(dependencies)

add_executable(HelloTextures ${HELLO_TEXTURES_FILES} ${HEADER_FILES})
target_link_libraries(HelloTextures glfw)

add_executable(HelloTextures4.5 ${HELLO_TEXTURES_FILES_4_5} ${HEADER_FILES})
target_link_libraries(HelloTextures4.5 glfw)

add_executable(HelloTriangle ${HELLO_TRIANGLE_FILES})
target_link_libraries(HelloTriangle glfw)

add_executable(HelloShaders ${HELLO_SHADERS_FILES})
target_link_libraries(HelloShaders glfw)