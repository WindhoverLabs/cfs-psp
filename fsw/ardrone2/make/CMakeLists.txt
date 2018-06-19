# Collect PSP includes and source
set(PSP_INC_DIRS 
	${CMAKE_CURRENT_SOURCE_DIR}/../inc
	${CMAKE_CURRENT_SOURCE_DIR}/../../inc
	PARENT_SCOPE)

add_subdirectory(../../shared psp/shared)
add_subdirectory(../src psp/platform)
	
set(PSP_SRC ${PSP_SHARED} ${PSP_PLATFORM} PARENT_SCOPE)

# Set libraries to link into the main executable
set(LIBS pthread dl rt PARENT_SCOPE)
    
# Set compiler flags for apps and the main executable.
set(COMPILE_FLAGS "-g" PARENT_SCOPE)
set(LINK_FLAGS "-g" PARENT_SCOPE) 

# the name of the target operating system
set(CMAKE_SYSTEM_NAME Linux)

# Setup cross compile
set(CMAKE_C_COMPILER $ENV{CFS_MISSION}/ardtool/bin/arm-cortex_a8-linux-gnueabi-gcc PARENT_SCOPE)
set(CMAKE_C_FLAGS "-g" PARENT_SCOPE)
set(CMAKE_CXX_COMPILER $ENV{CFS_MISSION}/ardtool/bin/arm-cortex_a8-linux-gnueabi-g++ PARENT_SCOPE)
set(CMAKE_CXX_FLAGS "-g" PARENT_SCOPE)
set(CMAKE_FIND_ROOT_PATH $ENV{CFS_MISSION}/ardtool/bin/arm-cortex_a8-linux-gnueabi/sysroot PARENT_SCOPE)
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER PARENT_SCOPE)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY PARENT_SCOPE)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY PARENT_SCOPE)


FUNCTION(add_library)
    _ADD_LIBRARY(${ARGN})
    #SET_TARGET_PROPERTIES(${ARGV0} PROPERTIES COMPILE_FLAGS ${COMPILE_FLAGS} LINK_FLAGS ${LINK_FLAGS} PREFIX "" )
ENDFUNCTION()
