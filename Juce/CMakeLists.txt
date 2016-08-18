# Juce Core
ADD_LIBRARY(juce_core STATIC "AppConfig.h;juce_core/juce_core.cpp;juce_core/juce_core.h")
TARGET_INCLUDE_DIRECTORIES(juce_core PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")
TARGET_INCLUDE_DIRECTORIES(juce_core PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/juce_core/")
PUT_IN_FOLDER_RELATIVE_ROOT(juce_core "${CMAKE_CURRENT_SOURCE_DIR}")

IF (APPLE)
	FIND_LIBRARY(COCOA_LIBRARY Cocoa)
	TARGET_LINK_LIBRARIES(juce_core ${COCOA_LIBRARY})
	FIND_LIBRARY(IOKIT_LIBRARY IOKit)
	TARGET_LINK_LIBRARIES(juce_core ${IOKIT_LIBRARY})
ENDIF()

## Juce Data Structures
#ADD_LIBRARY(juce_data_structures STATIC "AppConfig.h;juce_data_structures/juce_data_structures.cpp;juce_data_structures/juce_data_structures.h")
#TARGET_INCLUDE_DIRECTORIES(juce_data_structures PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
#TARGET_INCLUDE_DIRECTORIES(juce_data_structures PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/juce_data_structures/")
#PUT_IN_FOLDER_RELATIVE_ROOT(juce_data_structures "/juce")
#target_link_libraries("juce_data_structures" PUBLIC "juce_core")
#target_link_libraries("juce_data_structures" PUBLIC "juce_events")
#
## Juce Events
#ADD_LIBRARY(juce_events STATIC "AppConfig.h;juce_events/juce_events.cpp;juce_events/juce_events.h")
#TARGET_INCLUDE_DIRECTORIES(juce_events PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
#TARGET_INCLUDE_DIRECTORIES(juce_events PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/juce_events/")
#PUT_IN_FOLDER_RELATIVE_ROOT(juce_events "/juce")
#target_link_libraries("juce_events" PUBLIC "juce_core")
#
## Juce Graphics
#ADD_LIBRARY(juce_graphics STATIC "AppConfig.h;juce_graphics/juce_graphics.cpp;juce_graphics/juce_graphics.h")
#TARGET_INCLUDE_DIRECTORIES(juce_graphics PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
#TARGET_INCLUDE_DIRECTORIES(juce_graphics PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/juce_graphics/")
#PUT_IN_FOLDER_RELATIVE_ROOT(juce_graphics "/juce")
#target_link_libraries("juce_graphics" PUBLIC "juce_core")
#target_link_libraries("juce_graphics" PUBLIC "juce_events")
#
#IF (UNIX AND NOT APPLE) # AKA Linux
#	exec_program(freetype-config ARGS --cflags OUTPUT_VARIABLE FreetypeDef)
#	ADD_DEFINITIONS(${FreetypeDef})
#ENDIF()
#
#IF (APPLE)
#	FIND_LIBRARY(QUARTS_LIBRARY QuartzCore)
#	TARGET_LINK_LIBRARIES(juce_graphics ${QUARTS_LIBRARY})
#ENDIF()