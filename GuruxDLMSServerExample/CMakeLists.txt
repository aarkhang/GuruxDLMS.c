cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSServer VERSION 1.0
                  DESCRIPTION "Gurux DLMS Server example"
                  LANGUAGES C)

set(TARGET gurux_dlms_server)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
  include/connection.h
  include/getopt.h
  include/exampleserver.h
  src/getopt.c
  src/connection.c
  src/exampleserver.c
  src/main.c
)

target_link_libraries(${TARGET} PRIVATE
  gurux_dlms_c
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
