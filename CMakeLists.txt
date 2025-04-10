cmake_minimum_required(VERSION 3.7)
project(Filters)

include(filters.cmake)
set(CMAKE_BUILD_TYPE Release)
set(CMAKE_CXX_FLAGS "-O3 -Wall -Wextra")
set(CMAKE_C_FLAGS "-O3 -Wall -Wextra")
add_definitions(-fpic)

set(USE_DEBUG "-g")
set(USE_FLAGS "${USE_DEBUG}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${USE_FLAGS}")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${USE_FLAGS}")

#set(CMAKE_BUILD_TYPE Release)
#set(CMAKE_CXX_FLAGS "-O3 -Wall -Wextra")
#set(CMAKE_C_FLAGS "-O3 -Wall -Wextra")

SET(VORBIS_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/dec_vorbis.c
)

SET(VORBIS_INCLUDE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

SET(VORBIS_LIB
        ${CMAKE_CURRENT_SOURCE_DIR}/lib/libvorbis.a
        ${CMAKE_CURRENT_SOURCE_DIR}/lib/libogg.a
)

add_filter(vorbis
        "${VORBIS_SRC}"
        "${VORBIS_LIB}"
        []
        GPAC_HAS_VORBIS
        "${VORBIS_INCLUDE}"
        ""
        "1")
