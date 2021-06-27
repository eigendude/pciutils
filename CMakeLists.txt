################################################################################
#
#  Copyright (C) 2021 Garrett Brown
#  SPDX-License-Identifier: Apache-2.0
#
################################################################################


cmake_minimum_required(VERSION 3.5)
project(suspend-utils)

#
# Build step
#

add_custom_target(pci_utils ALL)

add_custom_command(
  TARGET pci_utils
  COMMAND make install-lib PREFIX="${CMAKE_CURRENT_BINARY_DIR}"
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

#
# Installed failes
#

install(
  DIRECTORY
    include/pci
  DESTINATION
    include/${PROJECT_NAME}
)

install(
  FILES
    lib/libpci.a
  DESTINATION
    lib/${PROJECT_NAME}
)
