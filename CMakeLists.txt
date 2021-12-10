cmake_minimum_required (VERSION 3.8.2)
project(imgui LANGUAGES CXX C)

add_library(imgui
    imgui.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
    imgui_tables.cpp
    imgui_spectrum.cpp
    $<$<BOOL:${IMGUI_DEMO}>:imgui_demo.cpp>
)

target_compile_definitions(imgui PUBLIC SPECTRUM_USE_DARK_THEME)
target_include_directories(imgui PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
