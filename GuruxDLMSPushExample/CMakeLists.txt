cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSCPush VERSION 1.0
                  DESCRIPTION "Gurux DLMS Push example"
                  LANGUAGES C)

set(TARGET gurux_dlms_push)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
    src/connection.c
    src/main.c
    include/connection.h
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
