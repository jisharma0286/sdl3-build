# SDL3 Build
#
# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

cmake_minimum_required (VERSION 3.16)

project("sdl3-build" C CXX)

add_library("sdl3-build" INTERFACE)

if (WIN32)
    if (CMAKE_BUILD_TYPE MATCHES Debug)
        list(APPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/windows/debug")
    else()
        list(APPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/windows/release")
    endif()
elseif (CMAKE_SYSTEM_NAME MATCHES Emscripten)
    if (CMAKE_BUILD_TYPE MATCHES Debug)
        list(APPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/emscripten/debug")
    else()
        list(APPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/emscripten/release")
    endif()
endif()

find_package(SDL3 REQUIRED)
target_link_libraries("sdl3-build" INTERFACE SDL3::SDL3)