# The contents of this file have been placed into the public domain; see the
# file COPYING for more details.

cmake_minimum_required (VERSION 3.0.2)
project (CppOtp)

# activate C++11 mode
if(CMAKE_CXX_COMPILER_ID STREQUAL Clang OR
	CMAKE_CXX_COMPILER_ID STREQUAL GNU OR
	CMAKE_CXX_COMPILER_ID STREQUAL AppleClang)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()

# the static library
add_library(cppotp STATIC
	src/libcppotp/bytes.cpp
	src/libcppotp/otp.cpp
	src/libcppotp/sha1.cpp
)

# the binary
add_executable(gauche
	src/gauche.cpp
)
target_link_libraries(gauche
	cppotp
)
