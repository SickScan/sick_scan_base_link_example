cmake_minimum_required (VERSION 3.10)
project(UserAPP)


list(APPEND CMAKE_PREFIX_PATH "${SSBL_INSTALL_DIR}")



find_package(ssbl REQUIRED)

set( APP_SRC
  ${PROJECT_SOURCE_DIR}/src/Main.cpp 
)

add_executable(${PROJECT_NAME} ${APP_SRC})
target_link_libraries(${PROJECT_NAME} ssbl::core::static)

if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
  if("${SSBL_32BIT}" )
    target_compile_options(${PROJECT_NAME} PRIVATE "$<$<CONFIG:DEBUG>:-m32>")
    target_compile_options(${PROJECT_NAME} PRIVATE "$<$<CONFIG:RELEASE>:-m32>")
  else()
    target_compile_options(${PROJECT_NAME} PRIVATE "$<$<CONFIG:DEBUG>:-m64>")
    target_compile_options(${PROJECT_NAME} PRIVATE "$<$<CONFIG:RELEASE>:-m64>")
  endif()
endif()

