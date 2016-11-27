# Disable warnings on Thirdparty libraries
if(MSVC)
	# Force to always compile with W0
	if(CMAKE_CXX_FLAGS MATCHES "/W[0-4]")
		string(REGEX REPLACE "/W[0-4]" "/W0" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
	else()
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /W0")
	endif()
elseif(CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
	# Update if necessary
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wno-long-long -pedantic")
endif()

add_subdirectory("Box2D")
add_subdirectory("FreeType")
add_subdirectory("Gainput")
add_subdirectory("GoogleTest")
add_subdirectory("Juce")
add_subdirectory("LibSass")
add_subdirectory("MoodyCamel")
#add_subdirectory("OGRE")
add_subdirectory("SDL")
add_subdirectory("Qt")
add_subdirectory("ZLib")

add_subdirectory("LibPNG") # Depends on ZLib
add_subdirectory("SDLImage") # Depends on SDL, ZLib, LibPNG
add_subdirectory("SDL2TTF") # Depends on SDL, FreeType