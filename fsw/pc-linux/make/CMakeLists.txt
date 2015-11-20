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
set(COMPILE_FLAGS "-m32 -g" PARENT_SCOPE)
set(LINK_FLAGS "-m32" PARENT_SCOPE) 

# the name of the target operating system
set(CMAKE_SYSTEM_NAME Linux)

# which compilers to use for C and C++
set(CMAKE_C_COMPILER gcc PARENT_SCOPE)
set(CMAKE_C_FLAGS "-m32 -g" PARENT_SCOPE)
set(CMAKE_CXX_COMPILER g++ PARENT_SCOPE)
set(CMAKE_CXX_FLAGS "-m32 -g" PARENT_SCOPE)