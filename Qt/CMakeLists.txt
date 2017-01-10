cmake_minimum_required(VERSION 2.8.11)
if (MSVC)
	if ("${WINXXBITS}" STREQUAL "Win64")
		if (${MSVC_VERSION} EQUAL 1900)
			set(QtPrefix "${CMAKE_CURRENT_SOURCE_DIR}/5.7/msvc2015_64/" CACHE INTERNAL "" FORCE)
		endif()
	endif()
endif()
if (CMAKE_COMPILER_IS_GNUCC) # GCC
	set(QtPrefix "${CMAKE_CURRENT_SOURCE_DIR}/5.7/gcc_64/" CACHE INTERNAL "" FORCE)
endif()


if (QtPrefix)
	MESSAGE("Qt has been found at ${QtPrefix}")
else()
	MESSAGE("No Qt binaries for current configuration")
endif()

MACRO(LINK_TO_QT projName)
	if (QtPrefix)	
		find_package(Qt5Widgets REQUIRED)
		
		target_link_libraries(Editor PUBLIC Qt5::Widgets)
		GET_TARGET_PROPERTY(interfaceIncludeDirectories Qt5::Widgets INTERFACE_INCLUDE_DIRECTORIES)
		if (interfaceIncludeDirectories)
			TARGET_INCLUDE_DIRECTORIES(${projName} PUBLIC ${interfaceIncludeDirectories})
		elseif(NOT ${dependency}_INCLUDES)
			MESSAGE("Warning: ${dependency} has no interface includes")
		endif()	
		
		add_custom_command(TARGET ${projName} POST_BUILD COMMAND ${CMAKE_COMMAND} -E copy_directory ${QtPrefix}/bin/ ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})
		add_custom_command(TARGET ${projName} POST_BUILD COMMAND ${CMAKE_COMMAND} -E copy_directory ${QtPrefix}/plugins/ ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/qt_plugins)
		if (NOT MSVC)
			add_custom_command(TARGET ${projName} POST_BUILD COMMAND ${CMAKE_COMMAND} -E copy_directory ${QtPrefix}/lib/ ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/lib)
		endif()

		source_group(automoc FILES "${CMAKE_CURRENT_BINARY_DIR}/${projName}_automoc.cpp" )
		
		MESSAGE("Linked Qt to ${projName}")
	endif()
ENDMACRO()

#Make macro globally visible
set(LINK_TO_QT "${LINK_TO_QT}" CACHE INTERNAL "" FORCE)

# Instruct CMake to run moc automatically when needed
set(CMAKE_AUTOMOC ON CACHE INTERNAL "" FORCE)

#Set these here, globally, so we don't need to set them every time we call the macro.
set("Qt5Widgets_DIR" "${QtPrefix}/lib/cmake/Qt5Widgets/" CACHE INTERNAL "" FORCE)
set("Qt5Gui_DIR" "${QtPrefix}/lib/cmake/Qt5Gui/" CACHE INTERNAL "" FORCE)
set("Qt5Core_DIR" "${QtPrefix}/lib/cmake/Qt5Core/" CACHE INTERNAL "" FORCE)

