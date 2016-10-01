add_subdirectory("Gainput")
add_subdirectory("GoogleTest")
add_subdirectory("Juce")
add_subdirectory("MoodyCamel")
#add_subdirectory("OGRE")
add_subdirectory("SDL")
add_subdirectory("Qt")
add_subdirectory("ZLib")

add_subdirectory("LibPNG") # Depends on ZLib
add_subdirectory("SDLImage") # Depends on SDL, ZLib, LibPNG