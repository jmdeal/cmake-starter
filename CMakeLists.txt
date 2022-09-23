cmake_minimum_required(VERSION 3.16)
project(CXX_Starter CXX C)

set(CMAKE_CXX_VERSION 17)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

include(FetchContent)

# Add fmt library
FetchContent_Declare(
    fmt
    GIT_REPOSITORY "https://github.com/fmtlib/fmt"
    # Release 9.1.0
    GIT_TAG "a33701196adfad74917046096bf5a2aa0ab0bb50"
)

foreach(content fmt)
    FetchContent_GetProperties(${content})
    string(TOLOWER "${content}" lc_name)
    if(NOT ${lc_name}_POPULATED)
        FetchContent_Populate(${content})
        add_subdirectory(${${lc_name}_SOURCE_DIR} ${${lc_name}_BINARY_DIR} EXCLUDE_FROM_ALL)
    endif()
endforeach()

add_subdirectory(src)
