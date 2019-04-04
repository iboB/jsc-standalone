add_library(javascriptcore INTERFACE)
target_include_directories(javascriptcore INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)
if("${CMAKE_SYSTEM_NAME}" STREQUAL "Windows")
    if(CMAKE_SIZEOF_VOID_P EQUAL 8)
        message(FATAL_ERROR "JSC-Standalone: Only 32-bit Windows builds are supported")
    else()
        set(lib ${CMAKE_CURRENT_SOURCE_DIR}/win/lib32)
        target_link_libraries(javascriptcore INTERFACE
            ${lib}/JavaScriptCore.lib
        )
    endif()
else()
    message(FATAL_ERROR "JSC-Standalone: Unsupported target platform")
endif()
