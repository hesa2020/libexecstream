
if(LIBEXECSTREAM_SHARED)
    set(libtype SHARED)
else()
    set(libtype STATIC)
endif()

find_package(Threads REQUIRED)

add_library(libexecstream ${libtype} exec-stream.cpp)
target_include_directories(libexecstream PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/../include")
target_link_libraries(libexecstream PUBLIC ${CMAKE_THREAD_LIBS_INIT})

if(NOT MSVC)
    target_compile_options(libexecstream PRIVATE -fPIC)
endif()
