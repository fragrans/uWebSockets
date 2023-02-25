cmake_minimum_required(VERSION 3.20.0)

project(uWebSockets VERSION 1.0.0)

find_package(libuv)

set(CMAKE_CXX_STANDARD 20)

#find_package(Boost COMPONENTS date_time filesystem system)

include_directories(${CMAKE_PREFIX_PATH}/include)
include_directories(${CMAKE_SOURCE_DIR}/uSockets/src/)
include_directories(${CMAKE_SOURCE_DIR}/src/)

FILE(GLOB UWS_FILES capi/*.cpp)
FILE(GLOB USOCKETS_FILES uSockets/src/*.c)

add_library(uSockets ${USOCKETS_FILES})
target_link_libraries(uSockets uv)

add_library(uWebSockets ${UWS_FILES})
add_dependencies(uWebSockets uSockets)

#target_link_libraries(uWebSockets uv)
#target_link_libraries(uWebSockets uSockets)
