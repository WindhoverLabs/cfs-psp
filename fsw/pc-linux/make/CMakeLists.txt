set(PSP_INC_DIRS 
	${CMAKE_CURRENT_SOURCE_DIR}/../inc
	${CMAKE_CURRENT_SOURCE_DIR}/../../inc
	PARENT_SCOPE)

add_subdirectory(../../shared psp/shared)
add_subdirectory(../src psp/platform)
	
SET(PSP_SRC ${PSP_SHARED} ${PSP_PLATFORM} PARENT_SCOPE)