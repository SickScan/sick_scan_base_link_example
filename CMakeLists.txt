cmake_minimum_required (VERSION 3.10)
project(UserAPP)


set (CMAKE_PREFIX_PATH "${SSBL_INSTALL_DIR}/cmake ${CMAKE_PREFIX_PATH}")

find_package(ssbl REQUIRED)

set( APP_SRC
  ${PROJECT_SOURCE_DIR}/src/Main.cpp 
)

add_executable(${PROJECT_NAME} ${APP_SRC})
target_link_libraries(${PROJECT_NAME} ssbl::ssbl)


