# cmake_minimum_required(VERSION 3.10)
# project(Basic)

# set(CMAKE_CXX_STANDARD 14)
# include_directories(/home/xuejun/anaconda3/include/gstreamer-1.0
#         /home/xuejun/anaconda3/include/glib-2.0/
#         /home/xuejun/anaconda3/lib/glib-2.0/include/)
# link_directories(/home/xuejun/anaconda3/lib/gstreamer-1.0)
# #include_directories(/home/xuejun/anaconda3/include/glib-2.0/glib.h)
# add_executable(Basic
#         basic_1.cpp)


cmake_minimum_required(VERSION 3.10)

project(gstreamer_01) #Project name

set(CMAKE_CXX_STANDARD 11) #setting C++ 11 standard
find_package(PkgConfig) #finding pkg-config is a helper tool

#using pkg-config to getting Gstreamer
pkg_check_modules(GSTREAMER REQUIRED gstreamer-1.0)

#including GStreamer header files directory
include_directories(
        ${GLIB_INCLUDE_DIRS}
        ${GSTREAMER_INCLUDE_DIRS}
)
message("include path is"${GLIB_INCLUDE_DIRS}, ${GSTREAMER_INCLUDE_DIRS})
#linking GStreamer library directory
link_directories(
        ${GLIB_LIBRARY_DIRS}
        ${GSTREAMER_LIBRARY_DIRS}
)
# message("link path is"${GLIB_LIBRARY_DIRS},${GSTREAMER_LIBRARY_DIRS})
message("library path is "${GSTREAMER_LIBRARIES})
#building target executable
add_executable(${PROJECT_NAME} 03_dynamic_pipline.cpp)

#linking Gstreamer library with target executable
target_link_libraries(${PROJECT_NAME} ${GSTREAMER_LIBRARIES})
