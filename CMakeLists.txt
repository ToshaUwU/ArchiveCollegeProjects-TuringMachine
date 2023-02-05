cmake_minimum_required(VERSION 3.11)

project(TuringMachine)
add_library(tmachine STATIC
	${CMAKE_CURRENT_SOURCE_DIR}/src/EndlessTape.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/src/Program.cpp
)

set_target_properties(tmachine PROPERTIES
	CXX_STANDARD 17
	CXX_STANDARD_REQUIRED YES
	CXX_EXTENSIONS NO

	RUNTIME_OUTPUT_DIRECTORY_DEBUG "${CMAKE_CURRENT_SOURCE_DIR}/bin/debug"
	RUNTIME_OUTPUT_DIRECTORY_RELEASE "${CMAKE_CURRENT_SOURCE_DIR}/bin/release"

	DEBUG_POSTFIX "-d"
	OUTPUT_NAME "tm"
)

if(MSVC)
	target_compile_options(tmachine PRIVATE /W4)
else()
	target_compile_options(tmachine PRIVATE -Wall -Wextra -Wpedantic)
endif()