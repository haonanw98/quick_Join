PROJECT(sigmod-contest)

CMAKE_MINIMUM_REQUIRED (VERSION 2.8)

ADD_COMPILE_OPTIONS(-g)
SET(CMAKE_CXX_STANDARD 14)
SET(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(CMAKE_CXX_EXTENSIONS OFF)

SET(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g -Wall ")
FIND_LIBRARY(libtbb tbb REQUIRED)

INCLUDE_DIRECTORIES(include)
ADD_SUBDIRECTORY(include)

ADD_EXECUTABLE(Joiner main.cpp )
TARGET_LINK_LIBRARIES(Joiner libalp ${libtbb})
ADD_EXECUTABLE(test test.cpp)
TARGET_LINK_LIBRARIES(test libalp ${libtbb})

INSTALL(TARGETS Joiner test
	DESTINATION ${CMAKE_CURRENT_SOURCE_DIR}/bin)
