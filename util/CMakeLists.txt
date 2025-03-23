add_executable(${yaml-cpp-target}-sandbox sandbox.cpp)
add_executable(${yaml-cpp-target}-parse parse.cpp)
add_executable(${yaml-cpp-target}-read read.cpp)

target_link_libraries(${yaml-cpp-target}-sandbox PRIVATE ${yaml-cpp-target})
target_link_libraries(${yaml-cpp-target}-parse PRIVATE ${yaml-cpp-target})
target_link_libraries(${yaml-cpp-target}-read PRIVATE ${yaml-cpp-target})

set_property(TARGET ${yaml-cpp-target}-sandbox PROPERTY OUTPUT_NAME sandbox)
set_property(TARGET ${yaml-cpp-target}-parse PROPERTY OUTPUT_NAME parse)
set_property(TARGET ${yaml-cpp-target}-read PROPERTY OUTPUT_NAME read)

set_target_properties(${yaml-cpp-target}-sandbox
  PROPERTIES
    CXX_STANDARD_REQUIRED ON
    OUTPUT_NAME sandbox)

set_target_properties(${yaml-cpp-target}-parse
  PROPERTIES
    CXX_STANDARD_REQUIRED ON
    OUTPUT_NAME parse)

set_target_properties(${yaml-cpp-target}-read
  PROPERTIES
    CXX_STANDARD_REQUIRED ON
    OUTPUT_NAME read)

if (NOT DEFINED CMAKE_CXX_STANDARD)
  set_target_properties(${yaml-cpp-target}-sandbox ${yaml-cpp-target}-parse ${yaml-cpp-target}-read
    PROPERTIES
      CXX_STANDARD 11)
endif()
