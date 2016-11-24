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

cmake_minimum_required(VERSION 2.8.3)
project(fzi_icl_comm)

find_package(icl_core REQUIRED COMPONENTS icl_core_config icl_core_logging icl_core)


# include the icl_hardware_can workspace
SET(ICMAKER_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/icmaker")
INCLUDE(${ICMAKER_DIRECTORY}/CMakeLists.txt)
ADD_SUBDIRECTORY (src/icl_comm)

# reset the project name as otherwise it would be IcMaker
project(fzi_icl_comm)

# install package.xml as we are a plain cmake package
install(FILES package.xml DESTINATION share/icl_hardware_comm)
