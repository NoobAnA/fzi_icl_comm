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

ICMAKER_SET("icl_comm" IDE_FOLDER ${ICL_COMM_IDE_FOLDER})

ICMAKER_ADD_SOURCES(
  ByteOrderConversion.cpp
  )

ICMAKER_ADD_HEADERS(
  ByteOrderConversion.h
  ImportExport.h
  )

IF (NOT WIN32)
  ICMAKER_ADD_SOURCES(
    InterfaceAddress.cpp
    )
    
  ICMAKER_ADD_HEADERS(
    InterfaceAddress.h
    )
ENDIF ()

ICMAKER_LOCAL_CPPDEFINES(-DICL_COMM_EXPORT_SYMBOLS)
ICMAKER_GLOBAL_CPPDEFINES(-D_IC_BUILDER_ICL_COMM_)
ICMAKER_INCLUDE_DIRECTORIES(${ICL_COMM_INCLUDE_DIRS})

ICMAKER_EXTERNAL_DEPENDENCIES(EXPORT
  Boost
  Boost_FILESYSTEM
  Boost_SYSTEM
)

ICMAKER_INTERNAL_DEPENDENCIES(
  icl_core
)

ICMAKER_BUILD_LIBRARY()
ICMAKER_INSTALL_HEADERS(${icmaker_target})
