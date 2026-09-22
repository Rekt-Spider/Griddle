cmake_minimum_required(VERSION 3.16)
project(Griddle)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

add_library(GLAD STATIC ${PROJECT_SOURCE_DIR}/../libs/glad/glad.c)
target_include_directories(GLAD PUBLIC
    ${PROJECT_SOURCE_DIR}/../libs
    ${PROJECT_SOURCE_DIR}/../libs/glad)

add_library(ImGui STATIC
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${PROJECT_SOURCE_DIR}/../libs/backends/imgui_impl_glfw.cpp
    ${PROJECT_SOURCE_DIR}/../libs/backends/imgui_impl_opengl3.cpp
)

target_include_directories(ImGui PUBLIC 
    ${IMGUI_DIR}
    ${PROJECT_SOURCE_DIR}/../libs/backends
    ${PROJECT_SOURCE_DIR}/../libs

)

include_directories(${PROJECT_SOURCE_DIR}/../libs/glm)

#TO DO: add libraries for core components



# Set C++20 standard for HandlerLib
target_compile_features(HandlerLib PUBLIC cxx_std_20)

# Define the executable
add_executable(Griddle main.cpp)

# Link libraries to the executable
target_link_libraries(Griddle
    #CORECOMPONENTLIBRARIES
    ImGui
    GLAD
    glfw
    OpenGL::GL
)

# Set C++20 standard for executable
target_compile_features(Systematicon PUBLIC cxx_std_20)
