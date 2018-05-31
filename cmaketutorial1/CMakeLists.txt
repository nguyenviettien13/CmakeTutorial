cmake_minimum_required (VERSION 2.6)
project (Tutorial)

configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )


# should we use our own math functions?
option (USE_MYMATH "Use tutorial provided math implementation" ON)

include_directories("${PROJECT_BINARY_DIR}")


# add the MathFunctions library?
#
if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
  add_library(MathFunctionslib MathFunctions/mysqrt.cpp )
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctionslib)
endif (USE_MYMATH)
 
# add the executable
add_executable (Tutorial tutorial.cpp)
target_link_libraries (Tutorial  ${EXTRA_LIBS})
