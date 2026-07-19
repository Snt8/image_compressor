cmake_minimum_required(VERSION 3.20)
project(image_compressor CXX C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_POLICY_VERSION_MINIMUM 3.5)

include(FetchContent)

FetchContent_Declare(
        raylib
        URL https://github.com/raysan5/raylib/archive/refs/tags/5.0.tar.gz
        DOWNLOAD_EXTRACT_TIMESTAMP TRUE
)

FetchContent_MakeAvailable(raylib)

add_executable(image_compressor
        src/include/stb_image.h
        src/include/stb_image_write.h
        src/core/compressor.c
        src/core/compressor.h
        src/processor/image_processor.cpp
        src/processor/image_processor.hpp
        src/tests/test.cpp
        src/ui/main.cpp
        src/ui/ui_manager.cpp
        src/ui/ui_manager.hpp
)

target_include_directories(image_compressor PRIVATE
        src/core
        src/processor
        src/include
        src/ui
)

target_link_libraries(image_compressor PRIVATE raylib)