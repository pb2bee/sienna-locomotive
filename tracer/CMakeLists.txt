find_package(DynamoRIO)

if (NOT DynamoRIO_FOUND)
  message(FATAL_ERROR "DynamoRIO package required to build")
endif(NOT DynamoRIO_FOUND)

add_library(tracer SHARED tracer.cpp utils.c)
target_compile_definitions(tracer PRIVATE -DUNICODE)

target_link_libraries(tracer Dbghelp)
target_link_libraries(tracer slcommon)

configure_DynamoRIO_client(tracer)

use_DynamoRIO_extension(tracer drmgr)
use_DynamoRIO_extension(tracer drreg)
use_DynamoRIO_extension(tracer drwrap)
use_DynamoRIO_extension(tracer drx)
use_DynamoRIO_extension(tracer droption)
