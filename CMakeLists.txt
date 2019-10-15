####################################################
#
# CMakeLists.txt for examples 
#
####################################################


cmake_minimum_required (VERSION 3.10)
project(ssbl-examples)


if(NOT DEFINED SSBL_INSTALL_DIR)
 set(SSBL_INSTALL_DIR ${PROJECT_SOURCE_DIR}/../../../install)
endif()