set(target_name loglib)
add_library(${target_name} STATIC "")
target_sources(${target_name}
PRIVATE
"${PROJECT_SOURCE_DIR}/src/log_lib/print_log.cpp"
PRIVATE 
"${PROJECT_SOURCE_DIR}/include/log_lib/print_log.h"
)
target_include_directories(${target_name} 
PUBLIC   
	$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
	$<BUILD_INTERFACE:${PROJECT_BINARY_DIR}>
	$<INSTALL_INTERFACE:include>
)

export(TARGETS ${target_name}
	FILE ${PROJECT_BINARY_DIR}/${target_name}_target.cmake
)

install(TARGETS ${target_name} EXPORT ${target_name} DESTINATION ${PROJECT_BINARY_DIR}/install/lib)
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ DESTINATION ${PROJECT_BINARY_DIR}/install/include/ )

#install(FILES ${PROJECT_BINARY_DIR}/FirstOrganizedCMakeConfig.h DESTINATION ${PROJECT_BINARY_DIR}/install/include/ )
#install export
#install(FILES ${PROJECT_BINARY_DIR}/FirstOrganizedCMakeConfig.cmake DESTINATION ${PROJECT_BINARY_DIR}/install/cmake/ )

install(EXPORT ${target_name} FILE loglib_target.cmake DESTINATION ${PROJECT_BINARY_DIR}/install/cmake/)









