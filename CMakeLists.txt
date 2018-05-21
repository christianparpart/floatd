cmake_minimum_required(VERSION 3.6)
project(floatd VERSION "0.0.0" LANGUAGES CXX)

# 3rdparty: fmtlib
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/fmt" EXCLUDE_FROM_ALL)
add_definitions(-DFMT_USE_WINDOWS_H=0)

# 3rdparty: Flow
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/flow")

if(UNIX)
  if(HAVE_ZLIB_H)
	  CHECK_LIBRARY_EXISTS(z deflate "" HAVE_LIBZ)
	  set(ZLIB_LIBRARIES z)
  endif(HAVE_ZLIB_H)
endif(UNIX)

include_directories(${CMAKE_CURRENT_BINARY_DIR}/src
                    ${CMAKE_CURRENT_SOURCE_DIR}/src)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/src/floatd/sysconfig.h.cmake
               ${CMAKE_CURRENT_BINARY_DIR}/src/floatd/sysconfig.h)

add_executable(floatd src/floatd/main.cc)
target_link_libraries(floatd FlowCore FlowLang)
set_target_properties(floatd PROPERTIES	CXX_STANDARD 17	CXX_STANDARD_REQUIRED ON)

install(TARGETS floatd DESTINATION "${CMAKE_INSTALL_PREFIX}/bin")
