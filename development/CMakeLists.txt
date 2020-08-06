cmake_minimum_required(VERSION 3.12)

project(GuruxDLMS_lib VERSION 1.0
                  DESCRIPTION "Gurux DLMS library"
                  LANGUAGES C)

set(TARGET gurux_dlms_c)

add_library(${TARGET} STATIC )

#Add this if used on microcontroller: GX_DLMS_MICROCONTROLLER
#Add this if you don't want to use malloc: DLMS_IGNORE_MALLOC
#Add this if you don't want to use object pointers: DLMS_IGNORE_OBJECT_POINTERS
#Add this if you want to use EPOC time: DLMS_USE_EPOCH_TIME
target_compile_definitions(${TARGET} PRIVATE
)

if(CMAKE_COMPILER_IS_GNUCXX)
  add_compile_options(
        -fPIC
        -Wno-unused-function
        -Wno-undef
  )
endif()

set(TARGET_SOURCES
    src/gxarray.c
    src/client.c
    src/gxsha1.c
    src/gxset.c
    src/server.c
    src/gxvalueeventargs.c
    src/gxkey.c
    src/ciphering.c
    src/dlms.c
    src/bytebuffer.c
    src/date.c
    src/bitarray.c
    src/parameters.c
    src/message.c
    src/cosem.c
    src/gxmd5.c
    src/apdu.c
    src/gxsha256.c
    src/gxobjects.c
    src/objectarray.c
    src/replydata.c
    src/gxaes.c
    src/gxinvoke.c
    src/converters.c
    src/serverevents.c
    src/notify.c
    src/variant.c
    src/dlmsSettings.c
    src/datainfo.c
    src/helpers.c
    src/gxget.c
)

set (TARGET_HEADERS
    include/objectarray.h
    include/gxignore.h
    include/notify.h
    include/gxsha1.h
    include/gxinvoke.h
    include/snparameters.h
    include/bytebuffer.h
    include/errorcodes.h
    include/client.h
    include/gxdefine.h
    include/gxobjects.h
    include/helpers.h
    include/gxkey.h
    include/gxmd5.h
    include/date.h
    include/apdu.h
    include/server.h
    include/dlmssettings.h
    include/replydata.h
    include/gxset.h
    include/enums.h
    include/crc.h
    include/gxaes.h
    include/cipheringenums.h
    include/bitarray.h
    include/gxint.h
    include/lnparameters.h
    include/serverevents.h
    include/message.h
    include/converters.h
    include/gxget.h
    include/datainfo.h
    include/ciphering.h
    include/gxsha256.h
    include/cosem.h
    include/gxvalueeventargs.h
    include/variant.h
    include/parameters.h
    include/gxarray.h
    include/dlms.h
    include/gxmem.h
)

target_sources( ${TARGET} PRIVATE
     ${TARGET_SOURCES}
     ${TARGET_HEADERS}
)
