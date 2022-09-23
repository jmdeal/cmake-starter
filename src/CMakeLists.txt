# File: src/CMakeLists.txt

set(BINARY_NAME sample)

add_executable(${BINARY_NAME} main.cc)
target_include_directories(${BINARY_NAME} PUBLIC .)
target_link_libraries(${BINARY_NAME} PUBLIC fmt)
