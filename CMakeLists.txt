project(game.libretro.dosbox)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(libretro-dosbox REQUIRED)

set(DEPBLIBS dosbox)

set(DOSBOX_CUSTOM_BINARY ${DOSBOX_LIB}
                         ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX}
                         dosbox)

build_addon(${PROJECT_NAME} DOSBOX DEPLIBS)

