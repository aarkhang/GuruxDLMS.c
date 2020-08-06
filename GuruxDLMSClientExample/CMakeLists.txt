cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSClient VERSION 1.0
                  DESCRIPTION "Gurux DLMS Client example"
                  LANGUAGES C)

set(TARGET gurux_dlms_client)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
    src/getopt.c
    src/connection.c
    src/communication.c
    src/main.c
    include/connection.h
    include/communication.h
    include/getopt.h
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
  )
endif()
