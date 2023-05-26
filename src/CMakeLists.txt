add_executable(ball main.cpp)

target_include_directories(ball PUBLIC "${CMAKE_SOURCE_DIR}/include")

target_link_libraries(ball PRIVATE small3d::small3d)

if(APPLE)
  set_target_properties(ball PROPERTIES LINK_FLAGS "-framework \
		AudioUnit -framework AudioToolbox -framework CoreAudio -framework Cocoa \
		-framework IOKit -framework CoreVideo")
endif()

if(MSVC)
  set_target_properties(ball PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY
    "${PROJECT_BINARY_DIR}/bin")
endif()
