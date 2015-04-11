PyAV
====

Pythonic bindings for [FFmpeg][ffmpeg]/[Libav][libav].

This branch provides windows support and can be compiled using [MinGW64][mingw].
To build it, do as follows:

1. Compile ffmpeg using the mingw64 compiler with **shared libraries** enabled.
1. Set the environment variable `PKG_CONFIG_PATH` to the where the pkgconf files for ffmpeg reside.  
    Example:  `set PKG_CONFIG_PATH=c:\ffmpeg_build\lib\pkgconfig`
1. Copy the following ffmpeg libraries to the `av` folder:  
      `avcodec-56.dll` `avdevice-56.dll` `avfilter-5.dll` `avformat-56.dll`  
      `avutil-54.dll` `postproc-53.dll` `swresample-1.dll` `swscale-3.dll`  
    Also copy the two dependent DLLs from mingw to the same folder:  
      `libgcc_s_dw2-1.dll` `libwinpthread-1.dll`
1. Build the project and create a self contained wheel archive that you can install on any machine.  
    `make wheel`
1. Install the package: `pip install dist/av-0.2.2-cp27-none-win32.whl`

*Note: don't try to import `av` while residing in the PyAV source folder, because it contains a directory named
... `av`, and its contents will be loaded instead of your newly build package. Change to some other directory
before using it, else python will get confused.*

[mingw]: http://mingw-w64.yaxm.org/
[ffmpeg]: http://ffmpeg.org/
[libav]: http://libav.org/

[![Build Status](https://secure.travis-ci.org/mikeboers/PyAV.png?branch=master)](https://travis-ci.org/mikeboers/PyAV)

Have fun, [Read the Docs](http://mikeboers.github.io/PyAV/), and good luck!
