cmake_minimum_required(VERSION 3.17)
set(CMAKE_CXX_STANDARD 20)
project(demo)

INCLUDE_DIRECTORIES(
        include
        /usr/local/mysql/include # mysql 头文件
        /opt/homebrew/Cellar/fmt/7.1.3/include
)

LINK_DIRECTORIES(
        /usr/local/mysql/lib
        /opt/homebrew/Cellar/fmt/7.1.3/lib
)

LINK_LIBRARIES(libmysqlclient.a)

# code insight 会失效
#set (demo_mmmalloc_dir demo_mmmalloc/*.h demo_mmmalloc/memlib.cpp)

add_executable(demo
        main.cpp
        ${demo_malloc_dir}
        demo_mmmalloc/mm.cpp
        demo_mmmalloc/heap.cpp
        demo_mmmalloc/heap.h
        demo_mmmalloc/mm.h
        demo_gcmalloc/gcmalloc.cpp
        demo_gcmalloc/gcmalloc.h
        )

target_link_libraries(demo libmysqlclient.a)

