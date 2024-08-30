cmake_minimum_required(VERSION 3.10)
project(Controller)

set(CMAKE_CXX_STANDARD 17)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

# 定义包含路径和库路径
set(RAYLIB_DIR "$ENV{HOME}/Code")
set(LIBS raylib GL m)

# 设置源文件和头文件
file(GLOB SOURCES "*.cpp")
file(GLOB HEADERS "*.h")

# 添加可执行文件
add_executable(controller ${SOURCES} ${HEADERS})

# 设置编译选项和链接库
target_compile_options(controller PRIVATE ${CFLAGS})
target_include_directories(
    controller
    PRIVATE
    .
    ${RAYLIB_DIR}/raylib/src
    ${RAYLIB_DIR}/raygui/src
)
target_link_directories(controller PRIVATE ${RAYLIB_DIR}/raylib/src)
target_link_libraries(controller PRIVATE ${LIBS})
