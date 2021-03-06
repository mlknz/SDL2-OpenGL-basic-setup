cmake_minimum_required(VERSION 3.0)
project(SDL2App)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Set the output folder where your program will be created
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})

find_package(Freetype REQUIRED)

# The following folder will be included
include_directories("${PROJECT_SOURCE_DIR}" ${FREETYPE_INCLUDE_DIRS})

# file(GLOB HEADERS renderer/Shader.h)
# file(GLOB yourProject_SRC *.h *.cpp)
# SOURCES += $$files(*.cpp) // haven't tried

#SET(GCC_COVERAGE_COMPILE_FLAGS "-ftest-coverage")
#SET(GCC_COVERAGE_LINK_FLAGS    "-lSDL2main -lSDL2 -lSDL2_image -lGLEW -lGLU -lGL")

SET( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}" )
#SET( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS}" )

SET( SOURCE_FILES
    ${HEADERS}
    ${PROJECT_SOURCE_DIR}/main.cpp
    ${PROJECT_SOURCE_DIR}/utils/appManager.cpp
    ${PROJECT_SOURCE_DIR}/controls/appControls.cpp
    ${PROJECT_SOURCE_DIR}/uiManager/uiManager.cpp
    ${PROJECT_SOURCE_DIR}/uiManager/button.cpp

    ${PROJECT_SOURCE_DIR}/renderer/appRenderer.cpp
    ${PROJECT_SOURCE_DIR}/renderer/textRenderer/textRenderer.cpp
    ${PROJECT_SOURCE_DIR}/renderer/shaderProgram.cpp
)
add_executable(hello ${SOURCE_FILES} )

TARGET_LINK_LIBRARIES(hello -lSDL2main -lSDL2 -lSDL2_image -lGLEW -lGLU -lGL ${FREETYPE_LIBRARIES})
