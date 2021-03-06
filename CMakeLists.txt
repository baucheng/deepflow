cmake_minimum_required(VERSION 3.1)
project(deepflow_release1_0_1)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -msse4")


set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

set(SOURCE_FILES
    deepflow.c
    image.c
    image.h
    io.c
    io.h
    opticalflow.c
    opticalflow.h
    opticalflow_aux.c
    opticalflow_aux.h
    README
    solver.c
    solver.h)


set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")
add_executable(fastdeepflow_release1_0_1 ${SOURCE_FILES})

target_link_libraries(fastdeepflow_release1_0_1 jpeg m png)


set(LIB_SOURCE_FILES
    io.c
    io.h
    image.h
    image.c
    opticalflow.c
    opticalflow.h
    opticalflow_aux.c
    opticalflow_aux.h
    solver.c
    solver.h
    )
add_library(libdeepflow SHARED ${LIB_SOURCE_FILES})

target_link_libraries(libdeepflow jpeg m png)
set_target_properties(libdeepflow PROPERTIES PREFIX "" OUTPUT_NAME "libdeepflow")
#caffe_default_properties(pycaffe)