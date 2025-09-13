cmake_minimum_required(VERSION 3.20)
project(swatmodflow Fortran)

set(CMAKE_VERBOSE_MAKEFILE ON)
#set(CMAKE_BUILD_TYPE Debug)
if(CMAKE_BUILD_TYPE STREQUAL "Release")
    set(TY "-Rel")
elseif(CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(TY "-Dbg")
else()
    set(TY "")
endif()

#set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -g -ffree-line-length-none -ffixed-line-length-none -fbacktrace -fbounds-check -Wall -Wextra")
set(fdialect        "-traceback -diag-disable=10448")
set(fdebug          "-warn all -check bounds")
set(frelease        "-O")
set(FFC             "ifo")
set(CMAKE_Fortran_FLAGS         "${CMAKE_Fortran_FLAGS} ${fdialect}")
set(CMAKE_Fortran_FLAGS_DEBUG   "${CMAKE_Fortran_FLAGS_DEBUG} ${fdebug}")
set(CMAKE_Fortran_FLAGS_RELEASE "${frelease}")

file(GLOB swat_src   swat/*.f    swat/*.f90)
file(GLOB modflow_src modflow/*.f modflow/*.f90)
file(GLOB rt3d_src    rt3d/*.f rt3d/*.f90)
file(GLOB smrt_src    smrt/*.f    smrt/*.f90)

set(SOURCE_FILES ${swat_src} ${modflow_src} ${rt3d_src} ${smrt_src})

add_executable(swatmodflow ${SOURCE_FILES})

set(INSTALL_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../bin)
install(TARGETS swatmodflow RUNTIME DESTINATION ${INSTALL_DIR})


