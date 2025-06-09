cmake_minimum_required(VERSION 3.25)

project(expected LANGUAGES CXX)

include(cmake/get_cpm.cmake)
include(GNUInstallDirs)

# CPMAddPackage("gh:repo/package1#REF")
# CPMAddPackage("gh:repo/package2#REF")

include(cmake/static_analyzers.cmake)

# set(expected_CompilerOptions ${expected_CompilerOptions})
# set(expected_LinkerOptions ${expected_LinkerOptions})

# set(expected_ExternalLibraries)

add_subdirectory(expected)
