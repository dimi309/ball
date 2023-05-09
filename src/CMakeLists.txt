add_executable(ball main.cpp)

target_include_directories(ball PUBLIC "${CMAKE_SOURCE_DIR}/include")

target_include_directories(ball PUBLIC ${SMALL3D_INCLUDE_DIRS})

target_link_libraries(ball PUBLIC ${SMALL3D_LIBRARIES})

if(APPLE)
  set_target_properties(ball PROPERTIES LINK_FLAGS "-framework \
		AudioUnit -framework AudioToolbox -framework CoreAudio -framework Cocoa \
		-framework IOKit -framework CoreVideo")
endif()

if(MSVC)
  set_target_properties(ball PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY
    "${PROJECT_BINARY_DIR}/bin")
endif()
