cmake_minimum_required(VERSION 3.8)

project(fmodbuild CXX C)

add_library(fmodbuild INTERFACE)
target_include_directories(fmodbuild INTERFACE "inc")

if (CMAKE_SYSTEM_NAME MATCHES Emscripten)
    target_link_directories(fmodbuild INTERFACE "lib/emscripten")
else()
    if (WIN32)
        target_link_directories(fmodbuild INTERFACE "lib/windows/x64")
    endif()
endif()

target_link_libraries(fmodbuild INTERFACE fmodstudioL)
