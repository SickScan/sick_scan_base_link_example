cmake_minimum_required (VERSION 3.10)
project(01_Hello_SSBL)


set (CMAKE_PREFIX_PATH "${SSBL_INSTALL_DIR}/cmake ${CMAKE_PREFIX_PATH}")


find_package(ssbl REQUIRED)

set( APP_SRC
  ${PROJECT_SOURCE_DIR}/src/Main.cpp 
)


add_executable(${PROJECT_NAME} ${TIM5XX_DEMO_SRC})
target_link_libraries(${PROJECT_NAME} ssbl::ssbl)


set_target_properties (${PROJECT_NAME} PROPERTIES FOLDER Basic)