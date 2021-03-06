# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

include_directories(${CMAKE_SOURCE_DIR}/libs/include)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library(
            avcodec-57
            SHARED
            IMPORTED
            )
add_library(
             avfilter-6
             SHARED
             IMPORTED
             )
add_library(
             avformat-57
             SHARED
             IMPORTED
             )
add_library(
             avutil-55
             SHARED
             IMPORTED
             )
add_library(
             swresample-2
             SHARED
             IMPORTED
             )
add_library(
             swscale-4
             SHARED
             IMPORTED
             )
add_library(
             avdevice-57
             SHARED
             IMPORTED
             )
add_library(
             postproc-54
             SHARED
             IMPORTED
             )

set_target_properties(
    avcodec-57
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libavcodec-57.so
    )
 set_target_properties(
     avfilter-6
     PROPERTIES IMPORTED_LOCATION
     ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libavfilter-6.so
     )
set_target_properties(
    avformat-57
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libavformat-57.so
    )
set_target_properties(
    avutil-55
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libavutil-55.so
    )
set_target_properties(
    swresample-2
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libswresample-2.so
    )
set_target_properties(
    swscale-4
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libswscale-4.so
    )
set_target_properties(
    avdevice-57
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libavdevice-57.so
    )
set_target_properties(
    postproc-54
    PROPERTIES IMPORTED_LOCATION
    ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/libpostproc-54.so
    )

add_library( # Sets the name of the library.
             ffbackSdk

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             src/main/cpp/native-lib.cpp )


# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       ffbackSdk

                       # Links the target library to the log library
                       # included in the NDK.
                       avcodec-57
                       avdevice-57
                       avfilter-6
                       avformat-57
                       avutil-55
                       postproc-54
                       swresample-2
                       swscale-4
                       -landroid
                       ${log-lib} )