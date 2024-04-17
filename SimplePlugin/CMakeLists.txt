cmake_minimum_required(VERSION 3.27)
project(SimplePlugin)

set(CMAKE_OSX_DEPLOYMENT_TARGET "10.12")
set(CMAKE_OSX_ARCHITECTURES x86_64)
set(CMAKE_CXX_STANDARD 17)
set(cxx_flags -Wno-ignored-attributes -mmacosx-version-min=10.12 -fvisibility=hidden -fno-threadsafe-statics -fno-rtti)

add_compile_options(
        "$<$<COMPILE_LANGUAGE:C>:${cxx_flags}>"
        "$<$<COMPILE_LANGUAGE:CXX>:${cxx_flags}>"
)

add_definitions(-DINTERNAL_CORE -DBGX)

add_library(SimplePlugin SHARED dllmain.cpp ../plugin_sdk/plugin_sdk.cpp ../plugin_sdk/clipper.cpp)
