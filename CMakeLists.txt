# Copyright (c) 2023-2024 Christian Hinkle, Brian Hinkle.

cmake_minimum_required(VERSION 3.24)

project(MeddySDKSuperbuild
  LANGUAGES CXX
  )

include(ExternalProject)

ExternalProject_Add(MeddySDK_Meddyproject
  SOURCE_DIR "${MeddySDKSuperbuild_SOURCE_DIR}/MeddySDK_Meddyproject"
  CMAKE_ARGS -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE} -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
  )

ExternalProject_Add(MeddySDKCLI
  DEPENDS MeddySDK_Meddyproject
  SOURCE_DIR "${MeddySDKSuperbuild_SOURCE_DIR}/MeddySDKCLI"
  CMAKE_ARGS -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE} -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
  )
