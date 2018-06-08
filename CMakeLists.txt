project(proto-sql)

if (${CMAKE_VERSION} VERSION_GREATER "3.9.6")
  cmake_minimum_required(VERSION 3.10)
endif()

include_directories(
  ${PROTOBUF_INCLUDE_DIRS}
  ${CMAKE_BINARY_DIR}/src/common/protobuf
  include
)
add_executable(proto-sql sql_code_generator.cpp proto-sql.cpp) 
find_library(protobuf HINTS /usr/lib/x86_64-linux-gnu)
find_library(protoc HINTS /usr/lib/x86_64-linux-gnu)
target_link_libraries(proto-sql protoc protobuf pthread ${PROTOBUF_LIBRARY})
