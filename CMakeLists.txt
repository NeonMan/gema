cmake_minimum_required (VERSION 2.6)
project (Gema)

##
## Compiler flags
##
add_definitions(-DNDEBUG)
add_definitions(-DTRACE)
set (CMAKE_C_FLAGS "-Wall -O2")

## Version.
set (Tutorial_VERSION_MAJOR 0)
set (Tutorial_VERSION_MINOR 0)

## Objects
set (SOURCES ${SOURCES} action.c)
set (SOURCES ${SOURCES} cstream.c)
set (SOURCES ${SOURCES} match.c)
set (SOURCES ${SOURCES} read.c)
set (SOURCES ${SOURCES} reg-expr.c)
set (SOURCES ${SOURCES} util.c)
set (SOURCES ${SOURCES} var.c)
set (SOURCES ${SOURCES} version.c)
set (SOURCES ${SOURCES} gema.c)

## Executables
add_executable (gema ${SOURCES})

## Install targets
install (TARGETS gema DESTINATION bin)
