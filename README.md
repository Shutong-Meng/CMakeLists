# CMakeLists
Attetion to write CMakeLists.txt
##
cmake_minimum_required（VERSION 2.8.3）
最低需要这个版本
##
project(...) 包名
##
find_package（catkin REQUIRED COMPONENTS ...)
若要访问另一个包，则加入包名，并且这种方法还会自动把该包的包含路劲加入catkin_INCLUDE_DIRS中
##
catkin_package(...)
在使用add_library()或add_executable()声明任何目标之前，必须调用此函数
有5个选择参数
catkin_package(
   INCLUDE_DIRS include      //导入文件夹include
   LIBRARIES ${PROJECT_NAME}   //项目中导出的库
   CATKIN_DEPENDS roscpp ...     //依赖的其他catkin项目
   DEPENDS eigen opencv ...       //依赖的非catkin的cmake项目
##
include_directories(${catkin_INCLUDE_DIRS})  //find_package生成的catkin_INCLUDE_DIRS以及其他需要再加入的目录
##
add_exectuble(${PROJECT_NAME}_node    ...)内
所有目标编译文件(.cpp)都要把路径写进去(src/...)生成可执行目标${PROJECT_NAME}_node
##
target_link_libraries(<executableTargetName>，<lib1>，<lib2>，... <libN>)
链接可执行文件与库，在add_exectuble之后，也可在之前加入add_library,
add_executable(foo src / foo.cpp)
add_library(moo src / moo.cpp)
target_link_libraries(foo moo)    链接foo与libmoo.so
一般target_link_libraries(${PROJECT_NAME}_node ${catkin_LIBRARIES})
##
生成器
add_message_files
add_service_files
add_action_files
之后要
generate_messages()
以上要在catkin_package()之前,且依赖message_runtime
catkin_package(
...
 CATKIN_DEPENDS message_runtime ...
...)
且
find_package(catkin REQUIRED COMPONENTS message_generation)
add_dependencies（${PROJECT_NAME}_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS}）
   
   
   
   
   
   
