cmake_minimum_required(VERSION 3.1)
project(pm-wrapper-interface CXX)
set(CMAKE_CXX_STANDARD 14) 
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
add_library(pm-wrapper-interface INTERFACE)
add_library(pm-wrapper-interface::pm-wrapper-interface ALIAS pm-wrapper-interface)
target_include_directories(pm-wrapper-interface INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)
install(TARGETS pm-wrapper-interface
    EXPORT pm-wrapper-interface-config)
install(EXPORT pm-wrapper-interface-config
    NAMESPACE pm-wrapper-interface::
    DESTINATION lib/cmake/pm-wrapper-interface)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/
    DESTINATION include)