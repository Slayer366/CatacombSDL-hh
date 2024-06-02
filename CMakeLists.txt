cmake_minimum_required(VERSION 3.19)
project(catacomb)

include(CheckFunctionExists)

set(SRC ${CMAKE_CURRENT_SOURCE_DIR})
set(BIN ${CMAKE_CURRENT_BINARY_DIR})

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -g -O0")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O0 -std=c++11")

include_directories()


link_directories(
  ${CMAKE_CURRENT_BINARY_DIR}
)

# Add all the files needed to compile here
add_executable(${PROJECT_NAME}
	cat_play.c
	catacomb.c
	catasm.c
	cpanel.c
	objects.c
	pcrlib_a.c
	pcrlib_c.c
	rleasm.c
)

# Library to link to (drop the -l prefix). This will mostly be stubs.
target_link_libraries(${PROJECT_NAME}
	SDL2
	SDL2_image
	SDL2_mixer
	m
	z
	jpeg
	png
	webp
	mikmod
	mpg123
	vorbis
	vorbisfile
	ogg
	pthread
	FLAC
)

target_include_directories(${PROJECT_NAME} PRIVATE
   "/usr/include/SDL2"
)
