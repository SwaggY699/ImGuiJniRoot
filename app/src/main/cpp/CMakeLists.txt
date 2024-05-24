# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.
cmake_minimum_required(VERSION 3.18.1)

# Declares and names the project.
project("imguijniroot")

# Sets compiler flags for the project.
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fvisibility=hidden")
set(CMAKE_C_VISIBILITY_PRESET hidden)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)

# Specifies the directories containing header files.
include_directories(
    draw
    imgui
    event
    backends
    /
)

# Specifies the source files.
file(GLOB_RECURSE native_srcs ./*.cpp)

# Creates and names a shared library.
add_library(
    imguijniroot
    SHARED
    ${native_srcs}
)

# Specifies the Android API level.
set(ANDROID_API_LEVEL "android-24")

# Specifies libraries CMake should link to your target library.
target_link_libraries(
    imguijniroot
    android
    EGL
    GLESv2
    log
)
