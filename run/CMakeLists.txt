add_executable(ckks_cpu_demo ckks_cpu_demo.cpp)
target_link_libraries(ckks_cpu_demo ckks_cpu)

install(TARGETS ckks_cpu_demo DESTINATION bin)
