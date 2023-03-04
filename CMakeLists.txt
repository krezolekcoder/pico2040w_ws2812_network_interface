cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(pico-helloworld C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(pico_ws2812_network_interface
main.c)

target_link_libraries(pico_ws2812_network_interface pico_stdlib)

pico_enable_stdio_uart(pico_ws2812_network_interface 1)

pico_add_extra_outputs(pico_ws2812_network_interface)

