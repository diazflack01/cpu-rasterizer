cmake_minimum_required(VERSION 3.12...3.16)

project(cpu-rasterizer VERSION 1.0
        DESCRIPTION "CPU Rasterizer"
        LANGUAGES CXX)

add_executable(cpu-rasterizer main.cpp TGAImage.cpp TGAImage.hpp Model.cpp Model.hpp Geometry.hpp)

add_custom_command(TARGET cpu-rasterizer POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        "${PROJECT_SOURCE_DIR}/model/"
        $<TARGET_FILE_DIR:cpu-rasterizer>/model/)