SET(SDL_STATIC false CACHE BOOL "" FORCE)

# Disable add_custom_target, otherwise SDL creates an uninstall target.
MACRO (add_custom_target)
ENDMACRO()

# Run default SDL CmakeLists.txt
add_subdirectory ("SDL2-2.0.4")

# Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("SDL2" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("SDL2main" "${CMAKE_CURRENT_SOURCE_DIR}")
#PUT_IN_FOLDER_RELATIVE_ROOT("SDL2-static" "${CMAKE_CURRENT_SOURCE_DIR}")

# Add generated config folder to public includes, so modules using SDL get it.
TARGET_INCLUDE_DIRECTORIES("SDL2" PUBLIC "${SDL2_BINARY_DIR}/include")
#TARGET_INCLUDE_DIRECTORIES("SDL2-static" PUBLIC "${SDL2_BINARY_DIR}/include")