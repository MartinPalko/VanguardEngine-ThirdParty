SET(PNG_TESTS OFF)
SET(PNG_STATIC ON)
SET(PNG_SHARED OFF)

add_subdirectory("lpng1625")
add_dependencies(png_static zlibstatic)
PUT_IN_FOLDER_RELATIVE_ROOT("png_static" "${CMAKE_CURRENT_SOURCE_DIR}")