#需求的最低cmake程序版本
cmake_minimum_required(VERSION 3.12)

#本工程的名字
project(Graphic)

#本工程支持的C++版本
set(CMAKE_CXX_STANDARD 17)

#file(GLOB copyResources "./assets")
#file(COPY ${copyResources} DESTINATION ${CMAKE_BINARY_DIR})

add_subdirectory(application)
add_subdirectory(gpu)

#本工程所有cpp文件编译链接，生成exe
add_executable(softRenderer "main.cpp")

target_link_libraries(softRenderer applicationLib gpuLib)

# ========= 资源管理（关键） =========
# 拷贝 assets 到运行目录
file(COPY
    ${CMAKE_CURRENT_SOURCE_DIR}/assets
    DESTINATION ${CMAKE_BINARY_DIR}
)

# 注入资源根目录给 C++,创建一个CMake变量ASSETS_RUNTIME_DIR，值为构建目录/assets
set(ASSETS_RUNTIME_DIR "${CMAKE_BINARY_DIR}/assets")

# 为softRenderer可执行文件定义预处理器宏
# DEBUG: 定义DEBUG宏，代码中可以用#ifdef DEBUG判断
# ASSETS_DIR: 定义为资源目录的路径
target_compile_definitions(softRenderer PRIVATE
    DEBUG
    ASSETS_DIR="${ASSETS_RUNTIME_DIR}"
)
