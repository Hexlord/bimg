project(bimg)
cmake_minimum_required(VERSION 3.8)

set(BIMG_ROOT "${CMAKE_CURRENT_SOURCE_DIR}" CACHE STRING "Description")

file(GLOB_RECURSE BIMG_SRC
	"src/*.inl"
	"src/*.h"
	"src/*.hpp"
	"src/*.c"
	"src/*.cpp"

#	"3rdparty/*.inl"
#	"3rdparty/*.h"
#	"3rdparty/*.hpp"
#	"3rdparty/*.c"
#	"3rdparty/*.cpp"

	"include/*.inl"
	"include/*.h"
	"include/*.hpp"
	"include/*.c"
	"include/*.cpp"
)

include_directories( include )
include_directories( 3rdparty )
include_directories( 3rdparty/iqa/include )
include_directories( 3rdparty/astc-codec/include )
include_directories( ${BX_ROOT}/include )

add_library(bimg STATIC
	${BIMG_SRC} 
)

set_target_properties(bimg PROPERTIES
	CLEAN_DIRECT_OUTPUT 1
)

target_link_libraries (bimg bx)
