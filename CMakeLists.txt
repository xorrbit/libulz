cmake_minimum_required(VERSION 2.8)

include (CheckIncludeFiles)

CHECK_INCLUDE_FILES(stdio.h HAVE_STDIO_H REQUIRED)
CHECK_INCLUDE_FILES(stdlib.h HAVE_STDLIB_H REQUIRED)
CHECK_INCLUDE_FILES(string.h HAVE_STRING_H REQUIRED)
CHECK_INCLUDE_FILES(stdint.h HAVE_STDINT_H REQUIRED)
CHECK_INCLUDE_FILES(errno.h HAVE_ERRNO_H REQUIRED)

message("Build Type      : ${CMAKE_BUILD_TYPE}")
message("Standard CFLAGS : ${CMAKE_C_FLAGS}")
message("Debug CFLAGS    : ${CMAKE_C_FLAGS_DEBUG}")
message("Release CFLAGS  : ${CMAKE_C_FLAGS_RELEASE}")

add_library(libulz STATIC ulz.c)
set_target_properties(libulz PROPERTIES OUTPUT_NAME "ulz")

install(TARGETS libulz DESTINATION lib)
install(FILES ulz.h DESTINATION include)
