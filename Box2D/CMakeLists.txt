SET(BOX2D_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory("Box2D/Box2D")

PUT_IN_FOLDER_RELATIVE_ROOT("Box2D" "${CMAKE_CURRENT_SOURCE_DIR}")