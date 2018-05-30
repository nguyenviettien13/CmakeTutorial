cmake_minimum_required (VERSION 2.6)
project (Tutorial)

configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )


include_directories("${PROJECT_BINARY_DIR}")
include_directories( "${PROJECT_SOURCE_DIR}/MathFunctions")
add_library(MathFunctionslib MathFunctions/mysqrt.cpp )

# add the executable
add_executable (Tutorial tutorial.cpp)
target_link_libraries (Tutorial MathFunctionslib)
