SET (FREETYPE_NO_DIST TRUE)
add_subdirectory("freetype-2.7")

PUT_IN_FOLDER_RELATIVE_ROOT("freetype" "${CMAKE_CURRENT_SOURCE_DIR}")