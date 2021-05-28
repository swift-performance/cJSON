#*************************************************************************
#
# SWIFT PERFORMANCE EQUIPMENT CONFIDENTIAL
# __________________
#
#  Copyright 2020 - 2021 Swift Performance Equipment
#  All Rights Reserved.
#
# NOTICE:  All information contained herein is, and remains
# the property of Swift Performance Equipment and its suppliers,
# if any.  The intellectual and technical concepts contained
# herein are proprietary to Swift Performance Equipment.
# and its suppliers and may be covered by U.S. and Foreign Patents,
# patents in process, and are protected by trade secret or copyright law.
# Dissemination of this information or reproduction of this material
# is strictly forbidden unless prior written permission is obtained
# from Swift Performance Equipment.
#

cmake_minimum_required(VERSION 3.13)

# use arm based toolchain configuration
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/toolchain.cmake)

if(CMAKE_HOST_SYSTEM_NAME STREQUAL Windows)
    set(TOOLCHAIN_PREFIX "C:/Program Files (x86)/Cypress/PSoC Creator/4.4/PSoC Creator/import/gnu/arm/5.4.1")
else()
    set(TOOLCHAIN_PREFIX "/usr/local")
endif()

set(CMAKE_BUILD_TYPE STRING DEBUG)
set(CMAKE_EXPORT_COMPILE_COMMANDS CACHE BOOL TRUE)

# FIR Filter library version
set(PROJECT_NAME cJSON)
set(LIBRARY_BINARY cjson)
project(${PROJECT_NAME} VERSION 1.7.14 LANGUAGES C)

# Set main source directory
set(PROJECT_SOURCE_DIR ../)

set(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS}")

message(STATUS "Building with CFLAGS \"${CMAKE_C_FLAGS})\"")

# Set sources for static library
add_library(${LIBRARY_BINARY} STATIC ${PROJECT_SOURCE_DIR}/cJSON_Utils.c ${PROJECT_SOURCE_DIR}/cJSON.c)