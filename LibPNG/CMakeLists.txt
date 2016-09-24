SET(PNG_TESTS OFF CACHE BOOL "" FORCE)
SET(PNG_STATIC OFF CACHE BOOL "" FORCE)
SET(PNG_SHARED ON CACHE BOOL "" FORCE)

add_subdirectory("lpng1625")
# add_dependencies(png_static zlibstatic)
# PUT_IN_FOLDER_RELATIVE_ROOT("png_static" "${CMAKE_CURRENT_SOURCE_DIR}")
add_dependencies(png zlibstatic)
PUT_IN_FOLDER_RELATIVE_ROOT("png" "${CMAKE_CURRENT_SOURCE_DIR}")