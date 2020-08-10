cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSServer2 VERSION 1.0
                  DESCRIPTION "Gurux DLMS Server example 2"
                  LANGUAGES C)

set(TARGET gurux_dlms_server2)

add_executable(${TARGET})

set(TOP_DIR ${PROJECT_SOURCE_DIR}/..)

target_sources( ${TARGET} PRIVATE
  include/getopt.h
  src/getopt.c
  src/main.c
)

target_compile_definitions(${TARGET} PRIVATE
  GX_DLMS_MICROCONTROLLER
  DLMS_USE_EPOCH_TIME
  DLMS_IGNORE_CLIENT
  DLMS_IGNORE_MALLOC
)

target_include_directories(${TARGET} PRIVATE
    ${TOP_DIR}/development/include
)

target_link_libraries(${TARGET} PRIVATE
  gurux_dlms_micro
)

if(WIN32)
  target_link_libraries(${TARGET} PRIVATE
     ws2_32
  )    
elseif(UNIX)
  target_link_libraries(${TARGET} PRIVATE
     m
     pthread
  )
endif()
