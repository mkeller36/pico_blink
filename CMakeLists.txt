cmake_minimum_required(VERSION 3.12)

if(DEFINED $ENV{PICO_SDK_PATH})
    message("pico sdk path is defined")
    include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)
else()
    message("pico sdk path not found")
    #${PICO_SDK_PATH}="~/.pico_sdk/pico-sdk"
    include(/home/mkeller/.pico_sdk/pico-sdk/external/pico_sdk_import.cmake)
endif()

project(blink_custom C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(${PROJECT_NAME}
    main.c
)

pico_add_extra_outputs(${PROJECT_NAME})

target_link_libraries(
    ${PROJECT_NAME}
    pico_stdlib
)