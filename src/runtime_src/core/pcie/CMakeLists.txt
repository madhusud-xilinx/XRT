# SPDX-License-Identifier: Apache-2.0
# Copyright (C) 2019-2021 Xilinx, Inc. All rights reserved.
#
include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}
  )

if(NOT WIN32)
  add_subdirectory(common)
  add_subdirectory(linux)
  add_subdirectory(tools)
  add_subdirectory(driver)
  if (${CMAKE_SYSTEM_PROCESSOR} STREQUAL "x86_64")
    # Emulation flow only works on x86_64
    add_subdirectory(emulation)
    add_subdirectory(noop)
  endif()
else()
  add_subdirectory(windows)
  add_subdirectory(tools)
endif(NOT WIN32)
