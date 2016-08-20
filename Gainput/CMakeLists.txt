SET (no_samples ON)
SET (no_test ON)

add_subdirectory ("${CMAKE_CURRENT_SOURCE_DIR}/gainput")

# Put all projects in the proper folder
PUT_IN_FOLDER_RELATIVE_ROOT("gainput" "${CMAKE_CURRENT_SOURCE_DIR}")
PUT_IN_FOLDER_RELATIVE_ROOT("gainputstatic" "${CMAKE_CURRENT_SOURCE_DIR}")
