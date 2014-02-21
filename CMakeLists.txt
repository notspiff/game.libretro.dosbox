project(gameclient.dosbox)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(dosbox
                    GIT_REPOSITORY https://github.com/libretro/dosbox-libretro
                    GIT_TAG 9c195a7
                    PREFIX dosbox
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -f Makefile.libretro
                    BUILD_IN_SOURCE 1)

set(DOSBOX_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/dosbox/src/dosbox/dosbox_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                         dosbox_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} dosbox)

build_addon(gameclient.dosbox DOSBOX DEPLIBS)
add_dependencies(gameclient.dosbox dosbox)
