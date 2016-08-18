# Disabled for now until it's needed.
SET (DIRECTX OFF)

# Run default SDL CmakeLists.txt
add_subdirectory ("${CMAKE_CURRENT_SOURCE_DIR}/SDL2-2.0.4")

# Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("SDL2" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("SDL2main" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("SDL2-static" "${CMAKE_CURRENT_SOURCE_DIR}")
