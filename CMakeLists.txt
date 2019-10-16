cmake_minimum_required (VERSION 3.10)
project(ssbl-project)


include(ExternalProject)


set(SSBL_PREFIX ${CMAKE_CURRENT_BINARY_DIR}/ssbl)
set(SSBL_GIT_REPO "https://github.com/SickScan/sick_scan_base.git")

set(SSBL_INSTALL_DIR ${CMAKE_CURRENT_BINARY_DIR}/ssbl-install)


ExternalProject_Add(SSBL-Debug
  PREFIX ${SSBL_PREFIX}
  BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}/ssbl-dbg-build
  GIT_REPOSITORY ${SSBL_GIT_REPO}
  GIT_TAG "master"
  GIT_PROGRESS ON
  UPDATE_COMMAND ""
  PATCH_COMMAND ""
  INSTALL_DIR ${SSBL_INSTALL_DIR}
  CMAKE_ARGS 
    -DCMAKE_BUILD_TYPE=Debug
    -DCMAKE_INSTALL_PREFIX=${SSBL_INSTALL_DIR}
)

ExternalProject_Add(SSBL-Release
  DEPENDS SSBL-Debug
  PREFIX ${SSBL_PREFIX}
  BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}/ssbl-rel-build
  GIT_REPOSITORY ${SSBL_GIT_REPO}
  GIT_TAG "master"
  GIT_PROGRESS ON
  UPDATE_COMMAND ""
  PATCH_COMMAND ""
  BUILD_COMMAND ""
  INSTALL_COMMAND
    cmake
    --build .
    --target install
    --config Release
        
  CMAKE_ARGS 
   -DCMAKE_BUILD_TYPE=Release
   -DCMAKE_INSTALL_PREFIX=${SSBL_INSTALL_DIR}
)

# Group targets nicely when using Visual Studio Community
set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set_target_properties (SSBL-Debug   PROPERTIES FOLDER Libary)
set_target_properties (SSBL-Release PROPERTIES FOLDER Libary)

#Add all examples
add_subdirectory(src)



