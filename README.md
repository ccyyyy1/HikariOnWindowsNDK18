# HikariOnWindowsNDK18
HikariOnWindowsNDK18 Patch


编译了一个 基于LLVM 7.0 的 Hikari，方便在windows 平台上使用， 已经继承到 NDK 18 中



使用方法：

1.先下载官方的 NDK 18.1.5063045 （可以从Android Studio 中下载，也可以从官网网页下载单独ZIP）
2.将  18.1.5063045.zip.001 ~ 18.1.5063045.zip.005 中的文件解压并覆盖官方的  18.1.5063045 文件夹下的内容
3.在android studio 项目中正确配置 ndk 为18.1.5063045   (可以新建一个 Native C++ 的空白项目来加入这些尝试调通）

app模块下的build.gradle

android {
...
    ndkVersion "18.1.5063045"
...
}


4.并添加一些CMAKE的编译选项

#混淆选项
#add_compile_options("-Wno-error=all")
#add_compile_options("-fno-elide-constructors")
set(CMAKE_C_FLAGS "-fno-elide-constructors ${CMAKE_C_FLAGS}")
#
## forevery
set(CMAKE_C_FLAGS "-O0 -v --verbose ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-bcfobf -mllvm -bcf_prob=70 ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-splitobf ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-strcry ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-cffobf ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-funcwra ${CMAKE_C_FLAGS}")
set(CMAKE_C_FLAGS "-mllvm -enable-subobf ${CMAKE_C_FLAGS}")

#
set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} ${CMAKE_CXX_FLAGS}")




下载

