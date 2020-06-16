add_executable(main main.c)

# 加入头文件搜索路径
include_directories(/usr/include/hello)

# 添加共享库的路径
target_link_libraries(main libhello.so)