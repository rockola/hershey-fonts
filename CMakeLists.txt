#
# hershey-fonts - Copyright (C) 2013 Kamal Mostafa <kamal@whence.com>
#
# License: GPL-2+
#

cmake_minimum_required(VERSION 2.8.12)

project(hershey-fonts)
set(hershey-fonts_VERSION_MAJOR 0)
set(hershey-fonts_VERSION_MINOR 1)

enable_testing()

file(GLOB jhf_files "hershey-fonts/*.jhf")
install(FILES ${jhf_files} DESTINATION share/hershey-fonts)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")

add_subdirectory(libhersheyfont)
add_subdirectory(tools)

## tests
foreach(jhf ${jhf_files})
  add_test("${jhf}" ${CMAKE_BINARY_DIR}/tools/hershey-font-check "${jhf}")
endforeach(jhf)

