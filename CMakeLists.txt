cmake_minimum_required(VERSION 2.8)

project(infra_project)

SET(INFRA_DIR src)

add_library(infra STATIC ${INFRA_DIR}/infra_vv_funcs.cpp ${INFRA_DIR}/infra_vm_funcs.cpp ${INFRA_DIR}/infra_mm_funcs.cpp ${INFRA_DIR}/infra_exception.cpp ${INFRA_DIR}/infra_binary.cpp)
target_include_directories (infra PUBLIC ${INFRA_DIR})

add_executable(tester tester/tester.cpp)

target_link_libraries(tester LINK_PUBLIC infra)

add_executable(tester_endian tester/tester_endian.cpp)

target_link_libraries(tester_endian LINK_PUBLIC infra)

install(TARGETS tester DESTINATION bin)
install(TARGETS tester_endian DESTINATION bin)