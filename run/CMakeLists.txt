add_executable(demo main.cpp)
target_link_libraries(demo ckks_cpu)

install(TARGETS demo DESTINATION bin)
