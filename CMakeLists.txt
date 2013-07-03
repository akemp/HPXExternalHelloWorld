# Require a recent version of cmake
cmake_minimum_required(VERSION 2.8.4 FATAL_ERROR)

# This project is C++ based.
project(HPXExternalHelloWorld)

# This adds the HPX cmake configuration directory to the search path.
set(CMAKE_MODULE_PATH
    $ENV{HPX_DIR}/share/cmake-2.8/Modules)

# Instruct cmake to find the HPX settings
find_package(HPX)

include_directories(${HPX_INCLUDE_DIR})
link_directories(${HPX_LIBRARY_DIR})


include_directories(external)

set (sources 
	hello_world/main.cpp
	external/EasyBMP/EasyBMP.cpp #for image output
	)
# add example executable
add_hpx_executable(hello_world
             SOURCES ${sources}
             ${SLICE_FLAGS} 
             FOLDER 
             COMPONENT_DEPENDENCIES)
