# this is for emacs file handling -*- mode: cmake; indent-tabs-mode: nil -*-

# -- BEGIN LICENSE BLOCK ----------------------------------------------
# This file is part of the SCHUNK SVH Driver suite.
#
# This program is free software licensed under the LGPL
# (GNU LESSER GENERAL PUBLIC LICENSE Version 3).
# You can find a copy of this license in LICENSE.txt in the top
# directory of the source code.
#
# © Copyright 2014 SCHUNK Mobile Greifsysteme GmbH, Lauffen/Neckar Germany
# © Copyright 2016 FZI Forschungszentrum Informatik, Karlsruhe, Germany
#
# -- END LICENSE BLOCK ------------------------------------------------

# this is for emacs file handling -*- mode: cmake; indent-tabs-mode: nil -*-

# To be used by other modules
SET(ICL_COMM_INCLUDE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/src" "${CMAKE_CURRENT_BINARY_DIR}/src" CACHE INTERNAL "")
SET(ICL_COMM_IDL_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/src" CACHE INTERNAL "")
SET(ICL_COMM_IDE_FOLDER "icl_comm")

IF("${CMAKE_SYSTEM_NAME}" STREQUAL "Windows")
  MESSAGE(STATUS "Package icl_comm has not been ported to Windows yet, ignoring.")
ELSE()
  ICMAKER_REGISTER_PACKAGE(icl_comm)

  ADD_SUBDIRECTORY (src/icl_comm)
  ADD_SUBDIRECTORY (src/icl_comm_serial)

  ICMAKER_CONFIGURE_PACKAGE()

ENDIF()
