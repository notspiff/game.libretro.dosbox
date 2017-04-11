cmake_minimum_required(VERSION 3.1)
project(game.libretro.dosbox)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

find_package(Kodi REQUIRED)
find_package(libretro-dosbox REQUIRED)

set(DOSBOX_CUSTOM_BINARY ${DOSBOX_LIB}
    ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX})

build_addon(${PROJECT_NAME} DOSBOX "")
