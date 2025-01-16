cmake_minimum_required(VERSION 3.28.3)

project(ckks_cpu CXX)

message("${CMAKE_BUILD_TYPE}")

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_SOURCE_DIR})
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -DNDEBUG")

cmake_path(SET ckks_cpu_headers_dir NORMALIZE ${CMAKE_CURRENT_SOURCE_DIR}/include)
cmake_path(SET ckks_cpu_sources_dir NORMALIZE ${CMAKE_CURRENT_SOURCE_DIR}/src)
aux_source_directory(${ckks_cpu_sources_dir} ckks_cpu_sources)

add_subdirectory(run)

add_library(ckks_cpu STATIC ${ckks_cpu_sources})
target_include_directories(ckks_cpu PUBLIC ${ckks_cpu_headers_dir})

install(TARGETS ckks_cpu DESTINATION lib)
# install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src/ DESTINATION include FILES_MATCHING PATTERN "*.h")

