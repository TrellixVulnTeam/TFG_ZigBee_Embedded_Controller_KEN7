cmake_minimum_required(VERSION 2.8)

project(mir-server)

set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -g -std=c++14 -Werror -Wall -fno-strict-aliasing -pedantic -Wnon-virtual-dtor -Wextra -fPIC")

include_directories(
    ${CMAKE_BINARY_DIR}/../install/usr/include/mirserver
    ${CMAKE_BINARY_DIR}/../install/usr/include/mirclient
    ${CMAKE_BINARY_DIR}/../install/usr/include/mircommon
    ${CMAKE_BINARY_DIR}/../install/usr/include/mirplatform
    ${CMAKE_BINARY_DIR}/../install/usr/include
)

add_executable(
    mir-server

    mir_server_window_management_info.cpp
    mir_server_fullscreen_wm.cpp
    mir_server_basic_window_manager.cpp
    mir_server.cpp
)

target_link_libraries(
    mir-server

    mirserver
    mirclient
    mircommon
)

install(TARGETS mir-server RUNTIME DESTINATION bin)
