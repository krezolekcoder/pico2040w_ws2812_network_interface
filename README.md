# pico2040w_ws2812_network_interface


# BUILD : 
mkdir build
cd build 
cmake ..  -DPICO_BOARD=pico_w -G"MinGW Makefiles"
make -j4

# FLASH using picoprobe 

openocd -s OPEN_OCD_SCRIPT_PATH -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c "adapter speed 5000" -c "program build/pico_ws2812_network_interface.hex verify reset exit"

OPEN_OCD_SCRIPT_PATH_EXAMPLE : C:\openocd-x64-standalone\scripts