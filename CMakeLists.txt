cmake_minimum_required(VERSION 3.25)

project(expected LANGUAGES CXX)

set(EXPORT_DIR "${CMAKE_SOURCE_DIR}/build/cmake")

include(cmake/CPM.cmake)
include(cmake/static_analyzers.cmake)
include(GNUInstallDirs)

# set(tl-expected_CompilerOptions ${tl-expected_CompilerOptions})
# set(tl-expected_LinkerOptions ${tl-expected_LinkerOptions})

# set(tl-expected_ExternalLibraries)

add_subdirectory(expected)
