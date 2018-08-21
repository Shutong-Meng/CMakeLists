# CMakeLists
Attetion to write CMakeLists.txt
##
add_exectuble(...)内
所有可执行文件(.cpp)都要把路径写进去(src/...)
##
find_package（catkin REQUIRED COMPONENTS ...)
若要访问另一个包，则加入包名，并且这种方法还会自动把该包的包含路劲加入catkin_INCLUDE_DIRS中
##
catkin_package(...)

