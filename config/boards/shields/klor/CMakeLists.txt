set_property(GLOBAL APPEND PROPERTY extra_post_build_commands
  COMMAND ${PYTHON_EXECUTABLE} ${ZEPHYR_BASE}/../tools/uf2/utils/uf2conv.py
  -c 
  -b 0x1000
  -f 0xADA52840
  -o ${PROJECT_BINARY_DIR}/${CONFIG_KERNEL_BIN_NAME}.uf2
  ${PROJECT_BINARY_DIR}/${CONFIG_KERNEL_BIN_NAME}.bin
)

target_sources_ifdef(CONFIG_CUSTOM_WIDGET_BATTERY_STATUS app PRIVATE battery_status.c)
target_sources_ifdef(CONFIG_CUSTOM_WIDGET_OUTPUT_STATUS app PRIVATE output_status.c)
target_sources_ifdef(CONFIG_CUSTOM_WIDGET_PROFILE_STATUS app PRIVATE profile_status.c)

zephyr_library()
zephyr_library_include_directories(${ZEPHYR_LVGL_MODULE_DIR})
zephyr_library_include_directories(${ZEPHYR_BASE}/lib/gui/lvgl/)
zephyr_library_sources(icons/bat_100.c)
zephyr_library_sources(icons/bat_100_c.c)
zephyr_library_sources(icons/bat_75.c)
zephyr_library_sources(icons/bat_75_c.c)
zephyr_library_sources(icons/bat_50.c)
zephyr_library_sources(icons/bat_50_c.c)
zephyr_library_sources(icons/bat_25.c)
zephyr_library_sources(icons/bat_25_c.c)
zephyr_library_sources(icons/bat_00.c)
zephyr_library_sources(icons/bat_00_c.c)
zephyr_library_sources(icons/usb_out.c)
zephyr_library_sources(icons/bt_out_nc.c)
zephyr_library_sources(icons/bt_out_ok.c)
zephyr_library_sources(icons/bt_out_search.c)
zephyr_library_sources(icons/bt_pro_0.c)
zephyr_library_sources(icons/bt_pro_1.c)
zephyr_library_sources(icons/bt_pro_2.c)
zephyr_library_sources(icons/bt_pro_3.c)
zephyr_library_sources(icons/bt_pro_4.c)
zephyr_library_sources(icons/klor_logo.c)
zephyr_library_sources_ifdef(CONFIG_ZMK_DISPLAY klor_status_screen.c)
zephyr_library_sources(${ZEPHYR_BASE}/misc/empty_file.c)
zephyr_library_include_directories(${CMAKE_SOURCE_DIR}/include)
zephyr_library_include_directories(${ZEPHYR_BASE}/drivers)
