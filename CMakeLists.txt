cmake_minimum_required(VERSION 3.25)

project(expected LANGUAGES CXX)

include(cmake/static_analyzers.cmake)
include(cmake/get_cpm.cmake)
include(GNUInstallDirs)

# set(tl-expected_CompilerOptions ${tl-expected_CompilerOptions})
# set(tl-expected_LinkerOptions ${tl-expected_LinkerOptions})

# CPMAddPackage("gh:repo/package1#REF")
# CPMAddPackage("gh:repo/package2#REF")
# ...
#
# set(tl-expected_ExternalLibraries)

add_subdirectory(expected)
