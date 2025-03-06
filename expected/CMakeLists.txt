add_subdirectory(include/tl)

add_library(${PROJECT_NAME} INTERFACE ${expected_HeaderFiles})
add_library(tl::expected ALIAS ${PROJECT_NAME})

if (ENABLE_CLANGTIDY)
    enable_clang_tidy(${PROJECT_NAME})
endif()

if (ENABLE_CPPCHECK)
    enable_cppcheck(${PROJECT_NAME})
endif()

target_include_directories(${PROJECT_NAME}
    INTERFACE
        "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
        "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>"
)

set_target_properties(${PROJECT_NAME} PROPERTIES VERIFY_INTERFACE_HEADER_SETS TRUE)

target_compile_features(${PROJECT_NAME} INTERFACE cxx_std_23)

target_sources(${PROJECT_NAME} PUBLIC FILE_SET HEADERS BASE_DIRS include FILES ${expected_HeaderFiles})

export(TARGETS      ${PROJECT_NAME}
       FILE         ${EXPORT_DIR}/${PROJECT_NAME}Targets.cmake
       NAMESPACE    tl::
)

install(TARGETS     ${PROJECT_NAME}
        EXPORT      ${PROJECT_NAME}Targets
        ARCHIVE
        FILE_SET HEADERS
        DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(EXPORT      ${PROJECT_NAME}Targets
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/${PROJECT_NAME}/cmake
        NAMESPACE   tl::
)

install(FILES ${PROJECT_SOURCE_DIR}/cmake/${PROJECT_NAME}Config.cmake
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/${PROJECT_NAME}/cmake
)

target_compile_options(${PROJECT_NAME} INTERFACE ${expected_CompilerOptions})
target_link_libraries(${PROJECT_NAME} INTERFACE ${expected_ExternalLibraries})
