
FILE(GLOB sourceFiles "libsass/src/*.*")
add_library("libsass" STATIC "${sourceFiles}")

TARGET_INCLUDE_DIRECTORIES("libsass" PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/libsass/include")

PUT_IN_FOLDER_RELATIVE_ROOT(libsass "${CMAKE_CURRENT_SOURCE_DIR}")