add_subdirectory ("zlib-1.2.8")

## Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("zlib" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("zlibstatic" "${CMAKE_CURRENT_SOURCE_DIR}")

# Make sure to include folder with generated zconf.h
TARGET_INCLUDE_DIRECTORIES("zlib" PUBLIC "${CMAKE_CURRENT_BINARY_DIR}/zlib-1.2.8/")
TARGET_INCLUDE_DIRECTORIES("zlibstatic" PUBLIC "${CMAKE_CURRENT_BINARY_DIR}/zlib-1.2.8/")

# Include directories for other libs
SET("ZLIB_INCLUDE_DIR" "${CMAKE_CURRENT_SOURCE_DIR}/zlib-1.2.8/;${CMAKE_CURRENT_BINARY_DIR}/zlib-1.2.8/" PARENT_SCOPE)
SET("ZLIB_LIBRARY" "$<TARGET_LINKER_FILE:zlibstatic>" PARENT_SCOPE)