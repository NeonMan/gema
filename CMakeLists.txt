cmake_minimum_required (VERSION 2.6)
project (Gema)

##
## Compiler flags
##
add_definitions(-DNDEBUG)
add_definitions(-DTRACE)
set (CMAKE_C_FLAGS "-Wall -O2")

## Version.
set (VERSION_MAJOR 1)
set (VERSION_MINOR 14)

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

## Targets
set (PKG_NAME "${CMAKE_PROJECT_NAME}_${VERSION_MAJOR}.${VERSION_MINOR}")
add_custom_target(dist
    COMMAND git archive --format tar.gz --prefix "${PKG_NAME}/" master -o "${PKG_NAME}.tar.gz")
add_custom_target(doc
    COMMAND cd doc && make && cd ..)
