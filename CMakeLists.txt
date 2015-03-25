cmake_minimum_required(VERSION 2.8)

project(infra_project)

SET(START_DIR .)

set( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${START_DIR}/builds/win32 )
set( CMAKE_LIBRARY_OUTPUT_DIRECTORY ${START_DIR}/builds/win32/lib )
set( CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${START_DIR}/builds/win32/lib )

SET(INFRA_DIR ${START_DIR}/src)

add_library(infra STATIC ${INFRA_DIR}/infra_vv_funcs.cpp ${INFRA_DIR}/infra_vm_funcs.cpp ${INFRA_DIR}/infra_mm_funcs.cpp ${INFRA_DIR}/infra_exception.cpp ${INFRA_DIR}/infra_binary.cpp)
target_include_directories (infra PUBLIC ${INFRA_DIR})

add_executable(tester ${START_DIR}/tester/tester.cpp)

target_link_libraries(tester LINK_PUBLIC infra)

add_executable(tester_endian ${START_DIR}/tester/tester_endian.cpp)

target_link_libraries(tester_endian LINK_PUBLIC infra)

install(TARGETS tester DESTINATION bin)
install(TARGETS tester_endian DESTINATION bin)