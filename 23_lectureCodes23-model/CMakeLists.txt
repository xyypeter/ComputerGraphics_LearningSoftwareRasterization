set(CMAKE_CXX_STANDARD 17)

include_directories(
    SYSTEM ${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/include
)

add_subdirectory(application)
add_subdirectory(gpu)

add_executable(softRenderer main.cpp)

target_link_libraries(softRenderer
    applicationLib
    gpuLib
    ${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/lib/assimp/assimp-vc143-mtd.lib
)

# ===== 拷贝 assets（必须是 POST_BUILD）=====
add_custom_command(TARGET softRenderer POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_CURRENT_SOURCE_DIR}/assets
    $<TARGET_FILE_DIR:softRenderer>/assets
)

# ===== 拷贝 DLL =====
add_custom_command(TARGET softRenderer POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/bin/assimp/assimp-vc143-mtd.dll
    $<TARGET_FILE_DIR:softRenderer>
)

# ===== 宏定义 =====
target_compile_definitions(softRenderer PRIVATE
    DEBUG
    ASSETS_DIR="$<TARGET_FILE_DIR:softRenderer>/assets"
)
