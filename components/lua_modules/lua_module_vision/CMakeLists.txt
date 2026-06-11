set(lua_module_vision_srcs
    "src/lua_module_vision.c"
)

set(lua_module_vision_requires
    cap_lua
    lua_module_image
)

if(CONFIG_LUA_MODULE_VISION_MOTION_DETECT)
    list(APPEND lua_module_vision_srcs
        "src/motion_detect.cpp"
    )
endif()

if(CONFIG_LUA_MODULE_VISION_ESPDET)
    list(APPEND lua_module_vision_srcs
        "src/espdet.cpp"
    )
    list(APPEND lua_module_vision_requires
        esp-dl
        freertos
    )
endif()

idf_component_register(
    SRCS
        ${lua_module_vision_srcs}
    INCLUDE_DIRS
        "src"
    REQUIRES
        ${lua_module_vision_requires}
)
