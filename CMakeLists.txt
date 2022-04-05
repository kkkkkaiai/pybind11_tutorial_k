cmake_minimum_required(VERSION 3.1)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_FLAGS "-O3")
set(CMAKE_CXX_FLAGS_RELEASE "-O3")


project(pybind11_tutorial)

add_subdirectory(pybind11)

include_directories("${CMAKE_SOURCE_DIR}/cpp/include/automobile_bits")
include_directories("${CMAKE_SOURCE_DIR}/python")

file (GLOB SOURCE_FILES "cpp/src/*.cpp")
file (GLOB HEADER_FILES "cpp/include/automobile_bits/*.hpp")
file (GLOB AUTOMOBILE_PYTHON_FILES "python/automobile/*.cpp" "python/automobile/*.hpp")

pybind11_add_module(automobile 
	${SOURCE_FILES}
	${HEADER_FILES}
	${AUTOMOBILE_PYTHON_FILES}
)

target_link_libraries(automobile PUBLIC)

pybind11_add_module(example1 python/example/01_cpp_vector/example.cpp)
pybind11_add_module(libcppex python/test/performance_test.cpp)

install(TARGETS automobile example1 libcppex
  COMPONENT python
  LIBRARY DESTINATION "${PYTHON_LIBRARY_DIR}"
)