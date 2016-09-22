
FILE(GLOB sourceFiles "SDL2_image-2.0.1/*.c"  "SDL2_image-2.0.1/*.h")

add_library("SDLImage" STATIC "${sourceFiles}")
add_definitions(-DLOAD_BMP)
add_definitions(-DLOAD_GIF)
#add_definitions(-DLOAD_JPG)
#add_definitions(-DLOAD_PNG)
add_definitions(-DLOAD_TGA)
#add_definitions(-DLOAD_TIF)
#add_definitions(-DLOAD_WEBP)

TARGET_INCLUDE_DIRECTORIES("SDLImage" PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/SDL2_image-2.0.1")

LINK_DEPENDENCY("SDLImage" "SDL2" false)
LINK_DEPENDENCY("SDLImage" "zlibstatic" true)
LINK_DEPENDENCY("SDLImage" "png_static" true)

PUT_IN_FOLDER_RELATIVE_ROOT(SDLImage "${CMAKE_CURRENT_SOURCE_DIR}")