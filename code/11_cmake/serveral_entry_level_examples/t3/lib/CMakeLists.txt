set(LIBHELLO_SRC hello.c)

# 构建动态库和静态库
add_library(hello SHARED ${LIBHELLO_SRC})
add_library(hello_static STATIC ${LIBHELLO_SRC})

# 设置静态库和动态库并存
SET_TARGET_PROPERTIES(hello_static PROPERTIES OUTPUT_NAME "hello")
set_target_properties(hello PROPERTIES CLEAN_DIRECT_OUTPUT 1)

# 控制动态库和静态库的版本
set_target_properties(hello PROPERTIES VERSION 1.2 SOVERSION 1)

# 安装头文件和动态静态库
install(
	TARGETS hello hello_static 
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
)
install(FILES hello.h DESTINATION include/hello)