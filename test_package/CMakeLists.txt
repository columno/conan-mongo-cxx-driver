project(test_package)
cmake_minimum_required(VERSION 3.1)

set(CMAKE_CXX_STANDARD 17)

if(MSVC)
  add_definitions(-D_ENABLE_EXTENDED_ALIGNED_STORAGE)
  add_definitions(-D_SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING)
  add_compile_options(/Zc:__cplusplus)
endif()

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})
