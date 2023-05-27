find_package(small3d REQUIRED)

add_executable(ball main.cpp)

target_link_libraries(ball PRIVATE small3d::small3d)

if(MSVC)
  set_target_properties(ball PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY
    "${PROJECT_BINARY_DIR}/bin")
endif()
