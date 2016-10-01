cmake_minimum_required (VERSION 2.8)


# Custom modules
set (CMAKE_MODULE_PATH "${CMAKE_INSTALL_PREFIX}/share/cmake/Modules" ${CMAKE_MODULE_PATH})


# Platform
include (platform)
initialize_platform ()


# Install
include (platform/install)


# Tests
include (platform/tests)
add_project_tests_main_target ()


# Documentation
include (platform/doxygen)
add_project_documentation_main_target ()


# 3rdparty
find_package (Qt4 4.7.1 COMPONENTS QtCore QtGui REQUIRED)
include (${QT_USE_FILE})
add_definitions (${QT_DEFINITIONS} -DQT_NO_CAST_FROM_ASCII)

find_package (EFC REQUIRED)
include_directories (${EFC_INCLUDE})

find_package (Lvfs REQUIRED)
include_directories (${LVFS_INCLUDE})


# Plugins
add_subdirectory (lvfs-arc)
add_subdirectory (lvfs-bits)
add_subdirectory (lvfs-db)
add_subdirectory (lvfs-qimg)
add_subdirectory (lvfs-qplayer)
