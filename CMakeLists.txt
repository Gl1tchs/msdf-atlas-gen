cmake_minimum_required(VERSION 3.25)

project(msdf-atlas-gen)

add_subdirectory(msdfgen)

file(GLOB_RECURSE SOURCE_FILES
    "msdf-atlas-gen/**.h"
    "msdf-atlas-gen/**.hpp"
    "msdf-atlas-gen/**.cpp"
)

add_library(msdf-atlas-gen STATIC ${SOURCE_FILES})

target_include_directories(msdf-atlas-gen PRIVATE
    msdf-atlas-gen
    msdfgen
    msdfgen/include
)

target_compile_definitions(msdf-atlas-gen PRIVATE
    _CRT_SECURE_NO_WARNINGS
)

target_link_libraries(msdf-atlas-gen PRIVATE
    msdfgen
)
