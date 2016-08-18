
## Run default OGRE CmakeLists.txt
add_subdirectory ("zlib-1.2.8")


## Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("zlib" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("zlibstatic" "${CMAKE_CURRENT_SOURCE_DIR}")


# Add include directory
#SET("zlibstatic_INCLUDES" "${CMAKE_CURRENT_SOURCE_DIR}/zlib-1.2.8/" PARENT_SCOPE)
#SET("zlib_INCLUDES" "${CMAKE_CURRENT_SOURCE_DIR}/zlib-1.2.8/" PARENT_SCOPE)