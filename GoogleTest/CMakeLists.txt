# Run default OGRE CmakeLists.txt
add_subdirectory ("${CMAKE_CURRENT_SOURCE_DIR}/gtest-1.7.0")

# Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("gtest" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("gtest_main" "${CMAKE_CURRENT_SOURCE_DIR}")
