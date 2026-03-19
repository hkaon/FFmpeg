# FFmpeg 8.1 Compile Configuration Reference

**Branch:** `release/8.1`
**License:** LGPL version 2.1 or later
**Architecture:** x86 (gcc/g++)

---

## Table of Contents

- [Component Summary](#component-summary)
- [Current Build Configuration](#current-build-configuration)
- [Configure Options Reference](#configure-options-reference)
  - [Standard Options](#standard-options)
  - [Licensing Options](#licensing-options)
  - [Configuration Options](#configuration-options)
  - [Program Options](#program-options)
  - [Documentation Options](#documentation-options)
  - [Component Options](#component-options)
  - [Individual Component Options](#individual-component-options)
  - [External Libraries](#external-libraries)
  - [Hardware Acceleration Libraries](#hardware-acceleration-libraries)
  - [Toolchain Options](#toolchain-options)
  - [Optimization Options](#optimization-options)
  - [Advanced Options](#advanced-options)
  - [Developer Options](#developer-options)
- [Full Component Lists](#full-component-lists)

---

## Component Summary

| Component              | Count |
|------------------------|------:|
| Decoders               |   607 |
| Encoders               |   275 |
| Demuxers               |   366 |
| Muxers                 |   184 |
| Filters                |   593 |
| Protocols              |    54 |
| Parsers                |    68 |
| Bitstream Filters      |    50 |
| Hardware Accelerators  |    77 |
| Input Devices          |    20 |
| Output Devices         |    10 |

---

## Current Build Configuration

The default build was produced with `--disable-x86asm`.

### Paths

| Setting  | Value        |
|----------|--------------|
| `prefix` | `/usr/local` |

### Compiler Toolchain

| Setting | Value |
|---------|-------|
| `ARCH`  | x86   |
| `CC`    | gcc   |
| `CXX`   | g++   |

### Enabled Libraries

- iconv
- zlib

### Enabled Features

- v4l2_m2m
- runtime_cpudetect
- safe_bitstream_reader
- static
- swscale_alpha
- unstable

### Enabled Components

- avdevice
- avfilter
- swscale
- avformat
- avcodec
- swresample
- avutil

### Enabled Programs

- ffprobe
- ffmpeg

### Enabled Input Devices

- fbdev
- lavfi
- oss
- v4l2

### Enabled Output Devices

- fbdev
- oss
- v4l2

---

## Configure Options Reference

### Standard Options

| Flag | Description |
|------|-------------|
| `--logfile=FILE` | Log tests and output to FILE (default: `ffbuild/config.log`) |
| `--disable-logging` | Do not log configure debug information |
| `--fatal-warnings` | Fail if any configure warning is generated |
| `--prefix=PREFIX` | Install in PREFIX (default: `/usr/local`) |
| `--bindir=DIR` | Install binaries in DIR (default: `PREFIX/bin`) |
| `--datadir=DIR` | Install data files in DIR (default: `PREFIX/share/ffmpeg`) |
| `--docdir=DIR` | Install documentation in DIR (default: `PREFIX/share/doc/ffmpeg`) |
| `--libdir=DIR` | Install libs in DIR (default: `PREFIX/lib`) |
| `--shlibdir=DIR` | Install shared libs in DIR (default: `LIBDIR`) |
| `--incdir=DIR` | Install includes in DIR (default: `PREFIX/include`) |
| `--mandir=DIR` | Install man page in DIR (default: `PREFIX/share/man`) |
| `--pkgconfigdir=DIR` | Install pkg-config .pc files in DIR (default: `LIBDIR/pkgconfig`) |
| `--enable-rpath` | Use rpath to allow installing libraries in paths not part of the dynamic linker search path |
| `--install-name-dir=DIR` | Darwin directory name for installed targets |

### Licensing Options

| Flag | Description |
|------|-------------|
| `--enable-gpl` | Allow use of GPL code; the resulting libs and binaries will be under GPL |
| `--enable-version3` | Upgrade (L)GPL to version 3 |
| `--enable-nonfree` | Allow use of nonfree code; the resulting binary will be unredistributable |

### Configuration Options

| Flag | Description |
|------|-------------|
| `--disable-static` | Do not build static libraries |
| `--enable-shared` | Build shared libraries |
| `--enable-small` | Optimize for size instead of speed |
| `--disable-runtime-cpudetect` | Disable detecting CPU capabilities at runtime (smaller binary) |
| `--enable-gray` | Enable full grayscale support (slower color) |
| `--disable-swscale-alpha` | Disable alpha channel support in swscale |
| `--disable-unstable` | Disable unstable API/ABI |
| `--disable-all` | Disable building components, libraries, and programs |
| `--disable-autodetect` | Disable automatically detected external libraries (re-enable individually) |

### Program Options

| Flag | Description |
|------|-------------|
| `--disable-programs` | Do not build command line programs |
| `--disable-ffmpeg` | Disable ffmpeg build |
| `--disable-ffplay` | Disable ffplay build |
| `--disable-ffprobe` | Disable ffprobe build |

### Documentation Options

| Flag | Description |
|------|-------------|
| `--disable-doc` | Do not build documentation |
| `--disable-htmlpages` | Do not build HTML documentation pages |
| `--disable-manpages` | Do not build man documentation pages |
| `--disable-podpages` | Do not build POD documentation pages |
| `--disable-txtpages` | Do not build text documentation pages |

### Component Options

| Flag | Description |
|------|-------------|
| `--disable-avdevice` | Disable libavdevice build |
| `--disable-avcodec` | Disable libavcodec build |
| `--disable-avformat` | Disable libavformat build |
| `--disable-swresample` | Disable libswresample build |
| `--disable-swscale` | Disable libswscale build |
| `--disable-avfilter` | Disable libavfilter build |
| `--disable-pthreads` | Disable pthreads (POSIX threads) |
| `--disable-w32threads` | Disable Win32 threads |
| `--disable-os2threads` | Disable OS/2 threads |
| `--disable-network` | Disable network support |
| `--disable-dwt` | Disable discrete wavelet transform |
| `--disable-error-resilience` | Disable error resilience code |
| `--disable-lsp` | Disable LSP code |
| `--disable-faan` | Disable floating-point AAN (I)DCT code |
| `--disable-iamf` | Disable IAMF (Immersive Audio Model and Formats) code |
| `--disable-pixelutils` | Disable pixel utils in libavutil |

### Individual Component Options

These flags allow fine-grained control over which individual codecs, muxers, demuxers, and other components are compiled into the build.

| Flag | Description |
|------|-------------|
| `--disable-everything` | Disable all components listed below |
| `--enable-encoder=NAME` / `--disable-encoder=NAME` | Enable or disable a specific encoder |
| `--enable-decoder=NAME` / `--disable-decoder=NAME` | Enable or disable a specific decoder |
| `--enable-hwaccel=NAME` / `--disable-hwaccel=NAME` | Enable or disable a specific hardware accelerator |
| `--enable-muxer=NAME` / `--disable-muxer=NAME` | Enable or disable a specific muxer |
| `--enable-demuxer=NAME` / `--disable-demuxer=NAME` | Enable or disable a specific demuxer |
| `--enable-parser=NAME` / `--disable-parser=NAME` | Enable or disable a specific parser |
| `--enable-bsf=NAME` / `--disable-bsf=NAME` | Enable or disable a specific bitstream filter |
| `--enable-protocol=NAME` / `--disable-protocol=NAME` | Enable or disable a specific protocol |
| `--enable-indev=NAME` / `--disable-indev=NAME` | Enable or disable a specific input device |
| `--enable-outdev=NAME` / `--disable-outdev=NAME` | Enable or disable a specific output device |
| `--enable-filter=NAME` / `--disable-filter=NAME` | Enable or disable a specific filter |

### External Libraries

The following flags enable support for external libraries. Each requires the corresponding library to be installed on the system.

| Flag | Description |
|------|-------------|
| `--enable-alsa` | Enable ALSA audio support (Linux) |
| `--enable-appkit` | Enable Apple AppKit framework |
| `--enable-avfoundation` | Enable Apple AVFoundation framework |
| `--enable-avisynth` | Enable reading of AviSynth script files |
| `--enable-bzlib` | Enable bzlib compression support |
| `--enable-cairo` | Enable Cairo graphics rendering |
| `--enable-coreimage` | Enable Apple CoreImage framework |
| `--enable-chromaprint` | Enable audio fingerprinting with chromaprint |
| `--enable-frei0r` | Enable frei0r video filtering |
| `--enable-gcrypt` | Enable gcrypt cryptographic library |
| `--enable-gmp` | Enable GNU MP arbitrary precision arithmetic |
| `--enable-gnutls` | Enable GnuTLS TLS/SSL support |
| `--enable-iconv` | Enable character encoding conversion via iconv |
| `--enable-jni` | Enable Java Native Interface |
| `--enable-ladspa` | Enable LADSPA audio filtering |
| `--enable-lcms2` | Enable ICC profile support via Little CMS 2 |
| `--enable-libaom` | Enable AV1 encoding/decoding via libaom |
| `--enable-libaribb24` | Enable ARIB STD-B24 caption decoding |
| `--enable-libaribcaption` | Enable ARIB caption decoding via libaribcaption |
| `--enable-libass` | Enable ASS/SSA subtitle rendering via libass |
| `--enable-libbluray` | Enable Blu-ray reading via libbluray |
| `--enable-libbs2b` | Enable Bauer stereophonic-to-binaural filter via libbs2b |
| `--enable-libcaca` | Enable text-based video output via libcaca |
| `--enable-libcelt` | Enable CELT decoding via libcelt |
| `--enable-libcdio` | Enable audio CD reading via libcdio |
| `--enable-libcodec2` | Enable Codec 2 encoding/decoding via libcodec2 |
| `--enable-libdav1d` | Enable AV1 decoding via libdav1d |
| `--enable-libdavs2` | Enable AVS2 decoding via libdavs2 |
| `--enable-libdc1394` | Enable IIDC-1394 (FireWire) camera input via libdc1394 |
| `--enable-libdvdnav` | Enable DVD navigation via libdvdnav |
| `--enable-libdvdread` | Enable DVD reading via libdvdread |
| `--enable-libfdk-aac` | Enable AAC encoding/decoding via Fraunhofer FDK AAC (nonfree) |
| `--enable-libflite` | Enable text-to-speech synthesis via flite |
| `--enable-libfontconfig` | Enable font configuration via libfontconfig |
| `--enable-libfreetype` | Enable font rendering via libfreetype |
| `--enable-libfribidi` | Enable Unicode BiDi support via libfribidi |
| `--enable-libharfbuzz` | Enable text shaping via libharfbuzz |
| `--enable-libglslang` | Enable GLSL to SPIR-V compilation via glslang |
| `--enable-libgme` | Enable Game Music Emu demuxing via libgme |
| `--enable-libgsm` | Enable GSM encoding/decoding via libgsm |
| `--enable-libiec61883` | Enable IEC 61883 (FireWire) input via libiec61883 |
| `--enable-libilbc` | Enable iLBC encoding/decoding via libilbc |
| `--enable-libjack` | Enable JACK audio input |
| `--enable-libjxl` | Enable JPEG XL encoding/decoding via libjxl |
| `--enable-libklvanc` | Enable VANC processing via libklvanc |
| `--enable-libkvazaar` | Enable HEVC encoding via libkvazaar |
| `--enable-liblc3` | Enable LC3 encoding/decoding via liblc3 |
| `--enable-liblcevc-dec` | Enable LCEVC decoding support |
| `--enable-liblensfun` | Enable lens distortion correction via liblensfun |
| `--enable-libmodplug` | Enable ModPlug module demuxing |
| `--enable-libmp3lame` | Enable MP3 encoding via LAME |
| `--enable-libmpeghdec` | Enable MPEG-H 3D Audio decoding via libmpeghdec |
| `--enable-liboapv` | Enable OAPV encoding via liboapv |
| `--enable-libopencore-amrnb` | Enable AMR-NB encoding/decoding via libopencore-amrnb |
| `--enable-libopencore-amrwb` | Enable AMR-WB decoding via libopencore-amrwb |
| `--enable-libopencv` | Enable video filtering via libopencv |
| `--enable-libopenh264` | Enable H.264 encoding/decoding via libopenh264 |
| `--enable-libopenjpeg` | Enable JPEG 2000 encoding/decoding via OpenJPEG |
| `--enable-libopenmpt` | Enable module demuxing via libopenmpt |
| `--enable-libopencolorio` | Enable OpenColorIO color management |
| `--enable-libopenvino` | Enable DNN inference via OpenVINO |
| `--enable-libopus` | Enable Opus encoding/decoding via libopus |
| `--enable-libplacebo` | Enable GPU-accelerated image processing via libplacebo |
| `--enable-libpulse` | Enable PulseAudio input/output |
| `--enable-libqrencode` | Enable QR code encoding via libqrencode |
| `--enable-libquirc` | Enable QR code decoding via libquirc |
| `--enable-librabbitmq` | Enable RabbitMQ support via librabbitmq |
| `--enable-librav1e` | Enable AV1 encoding via librav1e |
| `--enable-librist` | Enable RIST protocol via librist |
| `--enable-librsvg` | Enable SVG rasterization via librsvg |
| `--enable-librubberband` | Enable time-stretching and pitch-shifting via librubberband |
| `--enable-librtmp` | Enable RTMP streaming via librtmp |
| `--enable-libshaderc` | Enable GLSL to SPIR-V compilation via libshaderc |
| `--enable-libshine` | Enable fixed-point MP3 encoding via libshine |
| `--enable-libsmbclient` | Enable Samba protocol via libsmbclient |
| `--enable-libsnappy` | Enable Snappy compression via libsnappy |
| `--enable-libsoxr` | Enable audio resampling via libsoxr |
| `--enable-libspeex` | Enable Speex encoding/decoding via libspeex |
| `--enable-libsrt` | Enable SRT protocol via libsrt |
| `--enable-libssh` | Enable SFTP protocol via libssh |
| `--enable-libsvtav1` | Enable AV1 encoding via SVT-AV1 |
| `--enable-libsvtjpegxs` | Enable JPEG XS encoding/decoding via SVT-JPEG-XS |
| `--enable-libtensorflow` | Enable DNN inference via TensorFlow |
| `--enable-libtesseract` | Enable OCR via Tesseract |
| `--enable-libtheora` | Enable Theora encoding via libtheora |
| `--enable-libtls` | Enable TLS/SSL via libtls (LibreSSL) |
| `--enable-libtorch` | Enable DNN inference via libtorch (PyTorch C++) |
| `--enable-libtwolame` | Enable MP2 encoding via libtwolame |
| `--enable-libuavs3d` | Enable AVS3 decoding via libuavs3d |
| `--enable-libv4l2` | Enable V4L2 via libv4l2 wrapper |
| `--enable-libvidstab` | Enable video stabilization via vid.stab |
| `--enable-libvmaf` | Enable VMAF quality metric via libvmaf |
| `--enable-libvo-amrwbenc` | Enable AMR-WB encoding via libvo-amrwbenc |
| `--enable-libvorbis` | Enable Vorbis encoding/decoding via libvorbis |
| `--enable-libvpx` | Enable VP8/VP9 encoding/decoding via libvpx |
| `--enable-libvvenc` | Enable VVC encoding via libvvenc |
| `--enable-libwebp` | Enable WebP encoding via libwebp |
| `--enable-libx264` | Enable H.264 encoding via x264 (GPL) |
| `--enable-libx265` | Enable HEVC encoding via x265 (GPL) |
| `--enable-libxeve` | Enable EVC encoding via libxeve |
| `--enable-libxeveb` | Enable EVC baseline encoding via libxeve |
| `--enable-libxevd` | Enable EVC decoding via libxevd |
| `--enable-libxevdb` | Enable EVC baseline decoding via libxevd |
| `--enable-libxavs` | Enable AVS encoding via libxavs |
| `--enable-libxavs2` | Enable AVS2 encoding via libxavs2 |
| `--enable-libxcb` | Enable X11 grabbing using XCB |
| `--enable-libxcb-shm` | Enable XCB shared memory communication |
| `--enable-libxcb-xfixes` | Enable XCB xfixes for mouse rendering |
| `--enable-libxcb-shape` | Enable XCB shape extension |
| `--enable-libxvid` | Enable MPEG-4 encoding via libxvid (GPL) |
| `--enable-libxml2` | Enable XML parsing via libxml2 |
| `--enable-libzimg` | Enable image processing via z.lib (zimg) |
| `--enable-libzmq` | Enable ZeroMQ message passing |
| `--enable-libzvbi` | Enable teletext support via libzvbi |
| `--enable-lv2` | Enable LV2 audio filtering |
| `--enable-lzma` | Enable LZMA compression via liblzma |
| `--enable-decklink` | Enable Blackmagic DeckLink I/O |
| `--enable-mbedtls` | Enable TLS/SSL via mbedTLS |
| `--enable-mediacodec` | Enable Android MediaCodec hardware acceleration |
| `--enable-mediafoundation` | Enable Windows Media Foundation encoders |
| `--enable-metal` | Enable Apple Metal framework |
| `--enable-libmysofa` | Enable HRTF SOFA file support via libmysofa |
| `--enable-ohcodec` | Enable OpenHarmony media codec |
| `--enable-openal` | Enable OpenAL audio capture |
| `--enable-opencl` | Enable OpenCL processing |
| `--enable-opengl` | Enable OpenGL rendering |
| `--enable-openssl` | Enable TLS/SSL via OpenSSL |
| `--enable-pocketsphinx` | Enable speech recognition via PocketSphinx |
| `--enable-sndio` | Enable sndio audio I/O |
| `--enable-schannel` | Enable TLS/SSL via Windows Secure Channel |
| `--enable-sdl2` | Enable SDL2 for ffplay |
| `--enable-securetransport` | Enable TLS/SSL via Apple Secure Transport |
| `--enable-vapoursynth` | Enable VapourSynth demuxing |
| `--enable-whisper` | Enable speech recognition via whisper.cpp |
| `--enable-xlib` | Enable X11 interaction via Xlib |
| `--enable-zlib` | Enable zlib compression |

### Hardware Acceleration Libraries

| Flag | Description |
|------|-------------|
| `--enable-amf` | Enable AMD Advanced Media Framework |
| `--enable-audiotoolbox` | Enable Apple AudioToolbox codecs |
| `--enable-cuda-nvcc` | Enable CUDA compilation with nvcc |
| `--enable-cuda-llvm` | Enable CUDA compilation with LLVM/clang |
| `--enable-cuvid` | Enable NVIDIA CUVID video decoding |
| `--enable-d3d11va` | Enable Microsoft Direct3D 11 video acceleration |
| `--enable-d3d12va` | Enable Microsoft Direct3D 12 video acceleration |
| `--enable-dxva2` | Enable Microsoft DXVA 2 video acceleration |
| `--enable-ffnvcodec` | Enable NVIDIA codec headers (nvenc/nvdec) |
| `--enable-libdrm` | Enable DRM display support via libdrm |
| `--enable-libmfx` | Enable Intel MediaSDK (legacy QSV) |
| `--enable-libvpl` | Enable Intel VPL (modern QSV) |
| `--enable-libnpp` | Enable NVIDIA Performance Primitives |
| `--enable-mmal` | Enable Broadcom Multi-Media Abstraction Layer (Raspberry Pi) |
| `--enable-nvdec` | Enable NVIDIA hardware decoding |
| `--enable-nvenc` | Enable NVIDIA hardware encoding |
| `--enable-omx` | Enable OpenMAX IL |
| `--enable-omx-rpi` | Enable OpenMAX IL for Raspberry Pi |
| `--enable-rkmpp` | Enable Rockchip Media Process Platform |
| `--enable-v4l2-m2m` | Enable V4L2 memory-to-memory hardware codec |
| `--enable-vaapi` | Enable Video Acceleration API (Linux/Intel/AMD) |
| `--enable-vdpau` | Enable VDPAU (NVIDIA, Linux) |
| `--enable-videotoolbox` | Enable Apple VideoToolbox hardware acceleration |
| `--enable-vulkan` | Enable Vulkan-based processing |
| `--enable-vulkan-static` | Enable statically linked Vulkan support |

### Toolchain Options

| Flag | Description |
|------|-------------|
| `--arch=ARCH` | Select target architecture |
| `--cpu=CPU` | Select minimum required CPU (affects instruction selection) |
| `--cross-prefix=PREFIX` | Use PREFIX for compilation tools |
| `--progs-suffix=SUFFIX` | Program name suffix |
| `--enable-cross-compile` | Assume a cross-compiler is used |
| `--sysroot=PATH` | Root of cross-build tree |
| `--sysinclude=PATH` | Location of cross-build system headers |
| `--target-os=OS` | Compiler targets OS |
| `--target-exec=CMD` | Command to run executables on target |
| `--target-path=DIR` | Path to view of build directory on target |
| `--target-samples=DIR` | Path to samples directory on target |
| `--tempprefix=PATH` | Force fixed dir/prefix instead of mktemp for checks |
| `--toolchain=NAME` | Set tool defaults according to NAME (e.g., `gcc-asan`, `clang-msan`) |
| `--nm=NM` | Use nm tool NM |
| `--ar=AR` | Use archive tool AR |
| `--as=AS` | Use assembler AS |
| `--ln_s=LN_S` | Use symbolic link tool LN_S |
| `--strip=STRIP` | Use strip tool STRIP |
| `--windres=WINDRES` | Use Windows resource compiler WINDRES |
| `--x86asmexe=EXE` | Use x86 assembler EXE (nasm/yasm) |
| `--cc=CC` | Use C compiler CC |
| `--stdc=STANDARD` | Use specified C standard |
| `--cxx=CXX` | Use C++ compiler CXX |
| `--stdcxx=STANDARD` | Use specified C++ standard |
| `--objcc=OCC` | Use Objective-C compiler OCC |
| `--dep-cc=DEPCC` | Use dependency generator DEPCC |
| `--glslc=GLSLC` | Use GLSL compiler GLSLC |
| `--nvcc=NVCC` | Use NVIDIA CUDA compiler NVCC |
| `--ld=LD` | Use linker LD |
| `--metalcc=METALCC` | Use Metal compiler METALCC |
| `--metallib=METALLIB` | Use Metal library tool METALLIB |
| `--pkg-config=PKGCONFIG` | Use pkg-config tool PKGCONFIG |
| `--pkg-config-flags=FLAGS` | Pass additional flags to pkgconf |
| `--ranlib=RANLIB` | Use ranlib tool RANLIB |
| `--doxygen=DOXYGEN` | Use DOXYGEN to generate API doc |
| `--host-cc=HOSTCC` | Use host C compiler HOSTCC |
| `--host-cflags=HCFLAGS` | Use HCFLAGS when compiling for host |
| `--host-cppflags=HCPPFLAGS` | Use HCPPFLAGS when compiling for host |
| `--host-ld=HOSTLD` | Use host linker HOSTLD |
| `--host-ldflags=HLDFLAGS` | Use HLDFLAGS when linking for host |
| `--host-extralibs=HLIBS` | Use libs HLIBS when linking for host |
| `--host-os=OS` | Override host OS detection |
| `--extra-cflags=FLAGS` | Extra C compiler flags |
| `--extra-cxxflags=FLAGS` | Extra C++ compiler flags |
| `--extra-objcflags=FLAGS` | Extra Objective-C compiler flags |
| `--extra-ldflags=FLAGS` | Extra linker flags |
| `--extra-ldexeflags=FLAGS` | Extra linker flags for executables |
| `--extra-ldsoflags=FLAGS` | Extra linker flags for shared objects |
| `--extra-libs=LIBS` | Extra libraries to link |
| `--extra-version=STRING` | Extra version string to append |
| `--optflags=FLAGS` | Override optimization-related compiler flags |
| `--glslcflags=FLAGS` | GLSL compiler flags |
| `--nvccflags=FLAGS` | NVCC compiler flags |
| `--build-suffix=SUFFIX` | Library name suffix |
| `--enable-pic` | Build position-independent code |
| `--enable-thumb` | Compile for Thumb instruction set |
| `--enable-lto` | Enable link-time optimization |
| `--env=ENV` | Override the default environment variable(s) |
| `--disable-response-files` | Disable use of linker response files |

### Optimization Options

CPU instruction set toggles for architecture-specific optimizations.

**General:**

- `--disable-asm` -- Disable all assembly optimizations
- `--disable-inline-asm` -- Disable use of inline assembly
- `--disable-x86asm` -- Disable use of standalone x86 assembly (nasm/yasm)
- `--disable-fast-unaligned` -- Consider unaligned accesses slow
- `--disable-simd128` -- Disable WASM SIMD128 optimizations

**x86:**

`mmx`, `mmxext`, `sse`, `sse2`, `sse3`, `ssse3`, `sse4`, `sse42`, `avx`, `xop`, `fma3`, `fma4`, `avx2`, `avx512`, `avx512icl`, `aesni`, `clmul`

**ARM:**

`armv5te`, `armv6`, `armv6t2`, `vfp`, `neon`, `arm-crc`, `dotprod`, `i8mm`, `sve`, `sve2`, `sme`, `sme-i16i64`, `sme2`

**PowerPC:**

`altivec`, `vsx`, `power8`

**MIPS:**

`mipsdsp`, `mipsdspr2`, `msa`, `mipsfpu`, `mmi`

**LoongArch:**

`lsx`, `lasx`

**RISC-V:**

`rvv`

### Advanced Options

| Flag | Description |
|------|-------------|
| `--malloc-prefix=PREFIX` | Prefix malloc and related names with PREFIX |
| `--custom-allocator=NAME` | Use a supported custom allocator |
| `--disable-symver` | Disable symbol versioning |
| `--enable-hardcoded-tables` | Use hardcoded tables instead of runtime generation |
| `--disable-safe-bitstream-reader` | Disable bounds checking in bitreaders (faster, less safe) |
| `--sws-max-filter-size=N` | Maximum filter size for swscale |

### Developer Options

| Flag | Description |
|------|-------------|
| `--disable-debug` | Disable debugging symbols |
| `--enable-debug=LEVEL` | Set debugging level (0-3) |
| `--disable-optimizations` | Disable compiler optimizations |
| `--enable-extra-warnings` | Enable more compiler warnings |
| `--disable-stripping` | Disable stripping of executables and shared libraries |
| `--assert-level=LEVEL` | Set assert level (0=none, 1=most, 2=all) |
| `--enable-memory-poisoning` | Fill heap uninitialized allocated space with arbitrary data |
| `--valgrind=VALGRIND` | Run tests through Valgrind to detect memory leaks |
| `--enable-ftrapv` | Trap arithmetic overflows |
| `--samples=PATH` | Location of test samples (used by fate) |
| `--enable-neon-clobber-test` | Check NEON registers for clobbering (ARM) |
| `--enable-xmm-clobber-test` | Check XMM registers for clobbering (x86) |
| `--enable-random` | Randomly enable/disable components |
| `--disable-random` | Override `--enable-random` |
| `--random-seed=VALUE` | Seed value for `--enable/disable-random` |
| `--disable-valgrind-backtrace` | Do not print a backtrace under Valgrind |
| `--enable-ossfuzz` | Enable building fuzzer tool |
| `--libfuzzer=PATH` | Path to libfuzzer for fuzzing |
| `--ignore-tests=TESTS` | Comma-separated list of tests to ignore |
| `--enable-linux-perf` | Enable Linux performance monitor API |
| `--enable-macos-kperf` | Enable macOS kperf for performance monitoring |
| `--disable-large-tests` | Disable tests that use a large amount of memory |
| `--disable-shader-compression` | Disable shader compression |
| `--disable-resource-compression` | Disable resource compression |
| `--disable-version-tracking` | Disable version tracking in binaries |

---

## Full Component Lists

<details>
<summary><strong>Decoders (607)</strong></summary>

```
aac                    aac_at                 aac_fixed
aac_latm               aac_mediacodec         aasc
ac3                    ac3_at                 ac3_fixed
acelp_kelvin           adpcm_4xm              adpcm_adx
adpcm_afc              adpcm_agm              adpcm_aica
adpcm_argo             adpcm_circus           adpcm_ct
adpcm_dtk              adpcm_ea               adpcm_ea_maxis_xa
adpcm_ea_r1            adpcm_ea_r2            adpcm_ea_r3
adpcm_ea_xas           adpcm_g722             adpcm_g726
adpcm_g726le           adpcm_ima_acorn        adpcm_ima_alp
adpcm_ima_amv          adpcm_ima_apc          adpcm_ima_apm
adpcm_ima_cunning      adpcm_ima_dat4         adpcm_ima_dk3
adpcm_ima_dk4          adpcm_ima_ea_eacs      adpcm_ima_ea_sead
adpcm_ima_escape       adpcm_ima_hvqm2        adpcm_ima_hvqm4
adpcm_ima_iss          adpcm_ima_magix        adpcm_ima_moflex
adpcm_ima_mtf          adpcm_ima_oki          adpcm_ima_pda
adpcm_ima_qt           adpcm_ima_qt_at        adpcm_ima_rad
adpcm_ima_smjpeg       adpcm_ima_ssi          adpcm_ima_wav
adpcm_ima_ws           adpcm_ima_xbox         adpcm_ms
adpcm_mtaf             adpcm_n64              adpcm_psx
adpcm_psxc             adpcm_sanyo            adpcm_sbpro_2
adpcm_sbpro_3          adpcm_sbpro_4          adpcm_swf
adpcm_thp              adpcm_thp_le           adpcm_vima
adpcm_xa               adpcm_xmd              adpcm_yamaha
adpcm_zork             agm                    ahx
aic                    alac                   alac_at
alias_pix              als                    amrnb
amr_nb_at              amrnb_mediacodec       amrwb
amrwb_mediacodec       amv                    anm
ansi                   anull                  apac
ape                    apng                   aptx
aptx_hd                apv                    arbc
argo                   ass                    asv1
asv2                   atrac1                 atrac3
atrac3al               atrac3p                atrac3pal
atrac9                 aura                   aura2
av1                    av1_amf                av1_cuvid
av1_mediacodec         av1_qsv                avrn
avrp                   avs                    avui
bethsoftvid            bfi                    bink
binkaudio_dct          binkaudio_rdft         bintext
bitpacked              bmp                    bmv_audio
bmv_video              bonk                   brender_pix
c93                    cavs                   cbd2_dpcm
ccaption               cdgraphics             cdtoons
cdxl                   cfhd                   cinepak
clearvideo             cljr                   cllc
comfortnoise           cook                   cpia
cri                    cscd                   cyuv
dca                    dds                    derf_dpcm
dfa                    dfpwm                  dirac
dnxhd                  dolby_e                dpx
dsd_lsbf               dsd_lsbf_planar        dsd_msbf
dsd_msbf_planar        dsicinaudio            dsicinvideo
dss_sp                 dst                    dvaudio
dvbsub                 dvdsub                 dvvideo
dxa                    dxtory                 dxv
eac3                   eac3_at                eacmv
eamad                  eatgq                  eatgv
eatqi                  eightbps               eightsvx_exp
eightsvx_fib           escape124              escape130
evrc                   exr                    fastaudio
ffv1                   ffvhuff                ffwavesynth
fic                    fits                   flac
flashsv                flashsv2               flic
flv                    fmvc                   fourxm
fraps                  frwu                   ftr
g2m                    g723_1                 g728
g729                   gdv                    gem
gif                    gremlin_dpcm           gsm
gsm_ms                 gsm_ms_at              h261
h263                   h263i                  h263p
h263_v4l2m2m           h264                   h264_amf
h264_cuvid             h264_mediacodec        h264_mmal
h264_oh                h264_qsv               h264_rkmpp
h264_v4l2m2m           hap                    hca
hcom                   hdr                    hevc
hevc_amf               hevc_cuvid             hevc_mediacodec
hevc_oh                hevc_qsv               hevc_rkmpp
hevc_v4l2m2m           hnm4_video             hq_hqa
hqx                    huffyuv                hymt
iac                    idcin                  idf
iff_ilbm               ilbc                   ilbc_at
imc                    imm4                   imm5
indeo2                 indeo3                 indeo4
indeo5                 interplay_acm          interplay_dpcm
interplay_video        ipu                    jacosub
jpeg2000               jpegls                 jv
kgv1                   kmvc                   lagarith
lead                   libaom_av1             libaribb24
libaribcaption         libcelt                libcodec2
libdav1d               libdavs2               libfdk_aac
libgsm                 libgsm_ms              libilbc
libjxl                 libjxl_anim            liblc3
libmpeghdec            libopencore_amrnb      libopencore_amrwb
libopenh264            libopus                librsvg
libspeex               libsvtjpegxs           libuavs3d
libvorbis              libvpx_vp8             libvpx_vp9
libxevd                libzvbi_teletext       loco
lscr                   m101                   mace3
mace6                  magicyuv               mdec
media100               metasound              microdvd
mimic                  misc4                  mjpeg
mjpegb                 mjpeg_cuvid            mjpeg_qsv
mlp                    mmvideo                mobiclip
motionpixels           movtext                mp1
mp1_at                 mp1float               mp2
mp2_at                 mp2float               mp3
mp3adu                 mp3adufloat            mp3_at
mp3float               mp3_mediacodec         mp3on4
mp3on4float            mpc7                   mpc8
mpeg1_cuvid            mpeg1_v4l2m2m          mpeg1video
mpeg2_cuvid            mpeg2_mediacodec       mpeg2_mmal
mpeg2_qsv              mpeg2_v4l2m2m          mpeg2video
mpeg4                  mpeg4_cuvid            mpeg4_mediacodec
mpeg4_mmal             mpeg4_v4l2m2m          mpegvideo
mpl2                   msa1                   mscc
msmpeg4v1              msmpeg4v2              msmpeg4v3
msnsiren               msp2                   msrle
mss1                   mss2                   msvideo1
mszh                   mts2                   mv30
mvc1                   mvc2                   mvdv
mvha                   mwsc                   mxpeg
nellymoser             notchlc                nuv
on2avc                 opus                   osq
paf_audio              paf_video              pam
pbm                    pcm_alaw               pcm_alaw_at
pcm_bluray             pcm_dvd                pcm_f16le
pcm_f24le              pcm_f32be              pcm_f32le
pcm_f64be              pcm_f64le              pcm_lxf
pcm_mulaw              pcm_mulaw_at           pcm_s16be
pcm_s16be_planar       pcm_s16le              pcm_s16le_planar
pcm_s24be              pcm_s24daud            pcm_s24le
pcm_s24le_planar       pcm_s32be              pcm_s32le
pcm_s32le_planar       pcm_s64be              pcm_s64le
pcm_s8                 pcm_s8_planar          pcm_sga
pcm_u16be              pcm_u16le              pcm_u24be
pcm_u24le              pcm_u32be              pcm_u32le
pcm_u8                 pcm_vidc               pcx
pdv                    pfm                    pgm
pgmyuv                 pgssub                 pgx
phm                    photocd                pictor
pixlet                 pjs                    png
ppm                    prores                 prores_raw
prosumer               psd                    ptx
qcelp                  qdm2                   qdm2_at
qdmc                   qdmc_at                qdraw
qoa                    qoi                    qpeg
qtrle                  r10k                   r210
ra_144                 ra_288                 ralf
rasc                   rawvideo               realtext
rka                    rl2                    roq
roq_dpcm               rpza                   rscc
rtv1                   rv10                   rv20
rv30                   rv40                   rv60
s302m                  sami                   sanm
sbc                    scpr                   screenpresso
sdx2_dpcm              sga                    sgi
sgirle                 sheervideo             shorten
simbiosis_imx          sipr                   siren
smackaud               smacker                smc
smvjpeg                snow                   sol_dpcm
sonic                  sp5x                   speedhq
speex                  srgc                   srt
ssa                    stl                    subrip
subviewer              subviewer1             sunrast
svq1                   svq3                   tak
targa                  targa_y216             tdsc
text                   theora                 thp
tiertexseqvideo        tiff                   tmv
truehd                 truemotion1            truemotion2
truemotion2rt          truespeech             tscc
tscc2                  tta                    twinvq
txd                    ulti                   utvideo
v210                   v210x                  v308
v408                   v410                   vb
vble                   vbn                    vc1
vc1_cuvid              vc1image               vc1_mmal
vc1_qsv                vc1_v4l2m2m            vcr1
vmdaudio               vmdvideo               vmix
vmnc                   vnull                  vorbis
vp3                    vp4                    vp5
vp6                    vp6a                   vp6f
vp7                    vp8                    vp8_cuvid
vp8_mediacodec         vp8_qsv                vp8_rkmpp
vp8_v4l2m2m            vp9                    vp9_amf
vp9_cuvid              vp9_mediacodec         vp9_qsv
vp9_rkmpp              vp9_v4l2m2m            vplayer
vqa                    vqc                    vvc
vvc_qsv                wady_dpcm              wavarc
wavpack                wbmp                   wcmv
webp                   webvtt                 wmalossless
wmapro                 wmav1                  wmav2
wmavoice               wmv1                   wmv2
wmv3                   wmv3image              wnv1
wrapped_avframe        ws_snd1                xan_dpcm
xan_wc3                xan_wc4                xbin
xbm                    xface                  xl
xma1                   xma2                   xpm
xsub                   xwd                    y41p
ylc                    yop                    yuv4
zero12v                zerocodec              zlib
zmbv
```

</details>

<details>
<summary><strong>Encoders (275)</strong></summary>

```
a64multi               a64multi5              aac
aac_at                 aac_mf                 ac3
ac3_fixed              ac3_mf                 adpcm_adx
adpcm_argo             adpcm_g722             adpcm_g726
adpcm_g726le           adpcm_ima_alp          adpcm_ima_amv
adpcm_ima_apm          adpcm_ima_qt           adpcm_ima_ssi
adpcm_ima_wav          adpcm_ima_ws           adpcm_ms
adpcm_swf              adpcm_yamaha           alac
alac_at                alias_pix              amv
anull                  apng                   aptx
aptx_hd                ass                    asv1
asv2                   av1_amf                av1_d3d12va
av1_mediacodec         av1_mf                 av1_nvenc
av1_qsv                av1_vaapi              av1_vulkan
avrp                   avui                   bitpacked
bmp                    cfhd                   cinepak
cljr                   comfortnoise           dca
dfpwm                  dnxhd                  dpx
dvbsub                 dvdsub                 dvvideo
dxv                    eac3                   exr
ffv1                   ffv1_vulkan            ffvhuff
fits                   flac                   flashsv
flashsv2               flv                    g723_1
gif                    h261                   h263
h263p                  h263_v4l2m2m           h264_amf
h264_d3d12va           h264_mediacodec        h264_mf
h264_nvenc             h264_oh                h264_omx
h264_qsv               h264_rkmpp             h264_v4l2m2m
h264_vaapi             h264_videotoolbox      h264_vulkan
hap                    hdr                    hevc_amf
hevc_d3d12va           hevc_mediacodec        hevc_mf
hevc_nvenc             hevc_oh                hevc_qsv
hevc_rkmpp             hevc_v4l2m2m           hevc_vaapi
hevc_videotoolbox      hevc_vulkan            huffyuv
ilbc_at                jpeg2000               jpegls
libaom_av1             libcodec2              libfdk_aac
libgsm                 libgsm_ms              libilbc
libjxl                 libjxl_anim            libkvazaar
liblc3                 libmp3lame             liboapv
libopencore_amrnb      libopenh264            libopenjpeg
libopus                librav1e               libshine
libspeex               libsvtav1              libsvtjpegxs
libtheora              libtwolame             libvo_amrwbenc
libvorbis              libvpx_vp8             libvpx_vp9
libvvenc               libwebp                libwebp_anim
libx262                libx264                libx264rgb
libx265                libxavs                libxavs2
libxeve                libxvid                ljpeg
magicyuv               mjpeg                  mjpeg_qsv
mjpeg_vaapi            mlp                    movtext
mp2                    mp2fixed               mp3_mf
mpeg1video             mpeg2_qsv              mpeg2_vaapi
mpeg2video             mpeg4                  mpeg4_mediacodec
mpeg4_omx              mpeg4_v4l2m2m          msmpeg4v2
msmpeg4v3              msrle                  msvideo1
nellymoser             opus                   pam
pbm                    pcm_alaw               pcm_alaw_at
pcm_bluray             pcm_dvd                pcm_f32be
pcm_f32le              pcm_f64be              pcm_f64le
pcm_mulaw              pcm_mulaw_at           pcm_s16be
pcm_s16be_planar       pcm_s16le              pcm_s16le_planar
pcm_s24be              pcm_s24daud            pcm_s24le
pcm_s24le_planar       pcm_s32be              pcm_s32le
pcm_s32le_planar       pcm_s64be              pcm_s64le
pcm_s8                 pcm_s8_planar          pcm_u16be
pcm_u16le              pcm_u24be              pcm_u24le
pcm_u32be              pcm_u32le              pcm_u8
pcm_vidc               pcx                    pfm
pgm                    pgmyuv                 phm
png                    ppm                    prores
prores_aw              prores_ks              prores_ks_vulkan
prores_videotoolbox    qoi                    qtrle
r10k                   r210                   ra_144
rawvideo               roq                    roq_dpcm
rpza                   rv10                   rv20
s302m                  sbc                    sgi
smc                    snow                   sonic
sonic_ls               speedhq                srt
ssa                    subrip                 sunrast
svq1                   targa                  text
tiff                   truehd                 tta
ttml                   utvideo                v210
v308                   v408                   v410
vbn                    vc2                    vnull
vorbis                 vp8_mediacodec         vp8_v4l2m2m
vp8_vaapi              vp9_mediacodec         vp9_qsv
vp9_vaapi              wavpack                wbmp
webvtt                 wmav1                  wmav2
wmv1                   wmv2                   wrapped_avframe
xbm                    xface                  xsub
xwd                    y41p                   yuv4
zlib                   zmbv
```

</details>

<details>
<summary><strong>Demuxers (366)</strong></summary>

```
aa                     aac                    aax
ac3                    ac4                    ace
acm                    act                    adf
adp                    ads                    adx
aea                    afc                    aiff
aix                    alp                    amr
amrnb                  amrwb                  anm
apac                   apc                    ape
apm                    apng                   aptx
aptx_hd                apv                    aqtitle
argo_asf               argo_brp               argo_cvg
asf                    asf_o                  ass
ast                    au                     av1
avi                    avisynth               avr
avs                    avs2                   avs3
bethsoftvid            bfi                    bfstm
bink                   binka                  bintext
bit                    bitpacked              bmv
boa                    bonk                   brstm
c93                    caf                    cavsvideo
cdg                    cdxl                   cine
codec2                 codec2raw              concat
dash                   data                   daud
dcstr                  derf                   dfa
dfpwm                  dhav                   dirac
dnxhd                  dsf                    dsicin
dss                    dts                    dtshd
dv                     dvbsub                 dvbtxt
dvdvideo               dxa                    ea
eac3                   ea_cdata               epaf
evc                    ffmetadata             filmstrip
fits                   flac                   flic
flv                    fourxm                 frm
fsb                    fwse                   g722
g723_1                 g726                   g726le
g728                   g729                   gdv
genh                   gif                    gsm
gxf                    h261                   h263
h264                   hca                    hcom
hevc                   hls                    hnm
hxvs                   iamf                   ico
idcin                  idf                    iff
ifv                    ilbc                   image2
image2_alias_pix       image2_brender_pix     image2pipe
image_bmp_pipe         image_cri_pipe         image_dds_pipe
image_dpx_pipe         image_exr_pipe         image_gem_pipe
image_gif_pipe         image_hdr_pipe         image_j2k_pipe
image_jpegls_pipe      image_jpeg_pipe        image_jpegxl_pipe
image_jpegxs_pipe      image_pam_pipe         image_pbm_pipe
image_pcx_pipe         image_pfm_pipe         image_pgm_pipe
image_pgmyuv_pipe      image_pgx_pipe         image_phm_pipe
image_photocd_pipe     image_pictor_pipe      image_png_pipe
image_ppm_pipe         image_psd_pipe         image_qdraw_pipe
image_qoi_pipe         image_sgi_pipe         image_sunrast_pipe
image_svg_pipe         image_tiff_pipe        image_vbn_pipe
image_webp_pipe        image_xbm_pipe         image_xpm_pipe
image_xwd_pipe         imf                    ingenient
ipmovie                ipu                    ircam
iss                    iv8                    ivf
ivr                    jacosub                jpegxl_anim
jv                     kux                    kvag
laf                    lc3                    libgme
libmodplug             libopenmpt             live_flv
lmlm4                  loas                   lrc
luodat                 lvf                    lxf
m4v                    matroska               mca
mcc                    mgsts                  microdvd
mjpeg                  mjpeg_2000             mlp
mlv                    mm                     mmf
mods                   moflex                 mov
mp3                    mpc                    mpc8
mpegps                 mpegts                 mpegtsraw
mpegvideo              mpjpeg                 mpl2
mpsub                  msf                    msnwc_tcp
msp                    mtaf                   mtv
musx                   mv                     mvi
mxf                    mxg                    nc
nistsphere             nsp                    nsv
nut                    nuv                    obu
ogg                    oma                    osq
paf                    pcm_alaw               pcm_f32be
pcm_f32le              pcm_f64be              pcm_f64le
pcm_mulaw              pcm_s16be              pcm_s16le
pcm_s24be              pcm_s24le              pcm_s32be
pcm_s32le              pcm_s8                 pcm_u16be
pcm_u16le              pcm_u24be              pcm_u24le
pcm_u32be              pcm_u32le              pcm_u8
pcm_vidc               pdv                    pjs
pmp                    pp_bnk                 pva
pvf                    qcp                    qoa
r3d                    rawvideo               rcwt
realtext               redspark               rka
rl2                    rm                     roq
rpl                    rsd                    rso
rtp                    rtsp                   s337m
sami                   sap                    sbc
sbg                    scc                    scd
sdns                   sdp                    sdr2
sds                    sdx                    segafilm
ser                    sga                    shorten
siff                   simbiosis_imx          sln
smacker                smjpeg                 smush
sol                    sox                    spdif
srt                    stl                    str
subviewer              subviewer1             sup
svag                   svs                    swf
tak                    tedcaptions            thp
threedostr             tiertexseq             tmv
truehd                 tta                    tty
txd                    ty                     usm
v210                   v210x                  vag
vapoursynth            vc1                    vc1t
vividas                vivo                   vmd
vobsub                 voc                    vpk
vplayer                vqf                    vvc
w64                    wady                   wav
wavarc                 wc3                    webm_dash_manifest
webvtt                 wsaud                  wsd
wsvqa                  wtv                    wv
wve                    xa                     xbin
xmd                    xmv                    xvag
xwma                   yop                    yuv4mpegpipe
```

</details>

<details>
<summary><strong>Muxers (184)</strong></summary>

```
a64                    ac3                    ac4
adts                   adx                    aea
aiff                   alp                    amr
amv                    apm                    apng
aptx                   aptx_hd                apv
argo_asf               argo_cvg               asf
asf_stream             ass                    ast
au                     avi                    avif
avm2                   avs2                   avs3
bit                    caf                    cavsvideo
chromaprint            codec2                 codec2raw
crc                    dash                   data
daud                   dfpwm                  dirac
dnxhd                  dts                    dv
eac3                   evc                    f4v
ffmetadata             fifo                   filmstrip
fits                   flac                   flv
framecrc               framehash              framemd5
g722                   g723_1                 g726
g726le                 gif                    gsm
gxf                    h261                   h263
h264                   hash                   hds
hevc                   hls                    iamf
ico                    ilbc                   image2
image2pipe             ipod                   ircam
ismv                   ivf                    jacosub
kvag                   latm                   lc3
lrc                    m4v                    matroska
matroska_audio         mcc                    md5
microdvd               mjpeg                  mkvtimestamp_v2
mlp                    mmf                    mov
mp2                    mp3                    mp4
mpeg1system            mpeg1vcd               mpeg1video
mpeg2dvd               mpeg2svcd              mpeg2video
mpeg2vob               mpegts                 mpjpeg
mxf                    mxf_d10                mxf_opatom
null                   nut                    obu
oga                    ogg                    ogv
oma                    opus                   pcm_alaw
pcm_f32be              pcm_f32le              pcm_f64be
pcm_f64le              pcm_mulaw              pcm_s16be
pcm_s16le              pcm_s24be              pcm_s24le
pcm_s32be              pcm_s32le              pcm_s8
pcm_u16be              pcm_u16le              pcm_u24be
pcm_u24le              pcm_u32be              pcm_u32le
pcm_u8                 pcm_vidc               psp
rawvideo               rcwt                   rm
roq                    rso                    rtp
rtp_mpegts             rtsp                   sap
sbc                    scc                    segafilm
segment                smjpeg                 smoothstreaming
sox                    spdif                  spx
srt                    streamhash             stream_segment
sup                    swf                    tee
tg2                    tgp                    truehd
tta                    ttml                   uncodedframecrc
vc1                    vc1t                   voc
vvc                    w64                    wav
webm                   webm_chunk             webm_dash_manifest
webp                   webvtt                 whip
wsaud                  wtv                    wv
yuv4mpegpipe
```

</details>

<details>
<summary><strong>Filters (593)</strong></summary>

```
a3dscope               aap                    abench
abitscope              acompressor            acontrast
acopy                  acrossfade             acrossover
acrusher               acue                   addroi
adeclick               adeclip                adecorrelate
adelay                 adenorm                aderivative
adrawgraph             adrc                   adynamicequalizer
adynamicsmooth         aecho                  aemphasis
aeval                  aevalsrc               aexciter
afade                  afdelaysrc             afftdn
afftfilt               afir                   afireqsrc
afirsrc                aformat                afreqshift
afwtdn                 agate                  agraphmonitor
ahistogram             aiir                   aintegral
ainterleave            alatency               alimiter
allpass                allrgb                 allyuv
aloop                  alphaextract           alphamerge
amerge                 ametadata              amf_capture
amix                   amovie                 amplify
amultiply              anequalizer            anlmdn
anlmf                  anlms                  anoisesrc
anull                  anullsink              anullsrc
apad                   aperms                 aphasemeter
aphaser                aphaseshift            apsnr
apsyclip               apulsator              arealtime
aresample              areverse               arls
arnndn                 asdr                   asegment
aselect                asendcmd               asetnsamples
asetpts                asetrate               asettb
ashowinfo              asidedata              asisdr
asoftclip              aspectralstats         asplit
asr                    ass                    astats
astreamselect          asubboost              asubcut
asupercut              asuperpass             asuperstop
atadenoise             atempo                 atilt
atrim                  avectorscope           avgblur
avgblur_opencl         avgblur_vulkan         avsynctest
axcorrelate            azmq                   backgroundkey
bandpass               bandreject             bass
bbox                   bench                  bilateral
bilateral_cuda         biquad                 bitplanenoise
blackdetect            blackdetect_vulkan     blackframe
blend                  blend_vulkan           blockdetect
blurdetect             bm3d                   boxblur
boxblur_opencl         bs2b                   bwdif
bwdif_cuda             bwdif_vulkan           cas
ccrepack               cellauto               channelmap
channelsplit           chorus                 chromaber_vulkan
chromahold             chromakey              chromakey_cuda
chromanr               chromashift            ciescope
codecview              color                  colorbalance
colorchannelmixer      colorchart             colorcontrast
colorcorrect           colordetect            colorhold
colorize               colorkey               colorkey_opencl
colorlevels            colormap               colormatrix
colorspace             colorspace_cuda        colorspectrum
colortemperature       color_vulkan           compand
compensationdelay      concat                 convolution
convolution_opencl     convolve               copy
coreimage              coreimagesrc           corr
cover_rect             crop                   cropdetect
crossfeed              crystalizer            cue
curves                 datascope              dblur
dcshift                dctdnoiz               ddagrab
deband                 deblock                decimate
deconvolve             dedot                  deesser
deflate                deflicker              deinterlace_d3d12
deinterlace_qsv        deinterlace_vaapi      dejudder
delogo                 denoise_vaapi          derain
deshake                deshake_opencl         despill
detelecine             dialoguenhance         dilation
dilation_opencl        displace               dnn_classify
dnn_detect             dnn_processing         doubleweave
drawbox                drawbox_vaapi          drawgraph
drawgrid               drawtext               drawvg
drmeter                dynaudnorm             earwax
ebur128                edgedetect             elbg
entropy                epx                    eq
equalizer              erosion                erosion_opencl
estdif                 exposure               extractplanes
extrastereo            fade                   feedback
fftdnoiz               fftfilt                field
fieldhint              fieldmatch             fieldorder
fillborders            find_rect              firequalizer
flanger                flip_vulkan            flite
floodfill              format                 fps
framepack              framerate              framestep
freezedetect           freezeframes           frei0r
frei0r_src             fspp                   fsync
gblur                  gblur_vulkan           geq
gfxcapture             gradfun                gradients
graphmonitor           grayworld              greyedge
guided                 haas                   haldclut
haldclutsrc            hdcd                   headphone
hflip                  hflip_vulkan           highpass
highshelf              hilbert                histeq
histogram              hqdn3d                 hqx
hstack                 hstack_qsv             hstack_vaapi
hsvhold                hsvkey                 hue
huesaturation          hwdownload             hwmap
hwupload               hwupload_cuda          hysteresis
iccdetect              iccgen                 identity
idet                   il                     inflate
interlace              interlace_vulkan       interleave
join                   kerndeint              kirsch
ladspa                 lagfun                 latency
lcevc                  lenscorrection         lensfun
libplacebo             libvmaf                libvmaf_cuda
life                   limitdiff              limiter
loop                   loudnorm               lowpass
lowshelf               lumakey                lut
lut1d                  lut2                   lut3d
lutrgb                 lutyuv                 lv2
mandelbrot             maskedclamp            maskedmax
maskedmerge            maskedmin              maskedthreshold
maskfun                mcdeint                mcompand
median                 mergeplanes            mestimate
mestimate_d3d12        metadata               midequalizer
minterpolate           mix                    monochrome
morpho                 movie                  mpdecimate
mptestsrc              msad                   multiply
negate                 nlmeans                nlmeans_opencl
nlmeans_vulkan         nnedi                  noformat
noise                  normalize              null
nullsink               nullsrc                ocio
ocr                    ocv                    openclsrc
oscilloscope           overlay                overlay_cuda
overlay_opencl         overlay_qsv            overlay_vaapi
overlay_vulkan         owdenoise              pad
pad_cuda               pad_opencl             pad_vaapi
pal100bars             pal75bars              palettegen
paletteuse             pan                    perlin
perms                  perspective            phase
photosensitivity       pixdesctest            pixelize
pixscope               pp7                    premultiply
premultiply_dynamic    prewitt                prewitt_opencl
procamp_vaapi          program_opencl         pseudocolor
psnr                   pullup                 qp
qrencode               qrencodesrc            quirc
random                 readeia608             readvitc
realtime               remap                  remap_opencl
removegrain            removelogo             repeatfields
replaygain             reverse                rgbashift
rgbtestsrc             roberts                roberts_opencl
rotate                 rubberband             sab
scale                  scale2ref              scale2ref_npp
scale_cuda             scale_d3d11            scale_d3d12
scale_npp              scale_qsv              scale_vaapi
scale_vt               scale_vulkan           scdet
scdet_vulkan           scharr                 scroll
segment                select                 selectivecolor
sendcmd                separatefields         setdar
setfield               setparams              setpts
setrange               setsar                 settb
sharpen_npp            sharpness_vaapi        shear
showcqt                showcwt                showfreqs
showinfo               showpalette            showspatial
showspectrum           showspectrumpic         showvolume
showwaves              showwavespic           shuffleframes
shufflepixels          shuffleplanes          sidechaincompress
sidechaingate          sidedata               sierpinski
signalstats            signature              silencedetect
silenceremove          sinc                   sine
siti                   smartblur              smptebars
smptehdbars            sobel                  sobel_opencl
sofalizer              spectrumsynth          speechnorm
split                  spp                    sr
sr_amf                 ssim                   ssim360
stereo3d               stereotools            stereowiden
streamselect           subtitles              super2xsai
superequalizer         surround               swaprect
swapuv                 tblend                 telecine
testsrc                testsrc2               thistogram
threshold              thumbnail              thumbnail_cuda
tile                   tiltandshift           tiltshelf
tinterlace             tlut2                  tmedian
tmidequalizer          tmix                   tonemap
tonemap_opencl         tonemap_vaapi          tpad
transpose              transpose_npp          transpose_opencl
transpose_vaapi        transpose_vt           transpose_vulkan
treble                 tremolo                trim
unpremultiply          unsharp                unsharp_opencl
untile                 uspp                   v360
vaguedenoiser          varblur                vectorscope
vflip                  vflip_vulkan           vfrdet
vibrance               vibrato                vidstabdetect
vidstabtransform       vif                    vignette
virtualbass            vmafmotion             volume
volumedetect           vpp_amf                vpp_qsv
vstack                 vstack_qsv             vstack_vaapi
w3fdif                 waveform               weave
whisper                xbr                    xcorrelate
xfade                  xfade_opencl           xfade_vulkan
xmedian                xpsnr                  xstack
xstack_qsv             xstack_vaapi           yadif
yadif_cuda             yadif_videotoolbox     yaepblur
yuvtestsrc             zmq                    zoneplate
zoompan                zscale
```

</details>

<details>
<summary><strong>Protocols (54)</strong></summary>

```
android_content        async                  bluray
cache                  concat                 concatf
crypto                 data                   dtls
fd                     ffrtmpcrypt            ffrtmphttp
file                   ftp                    gopher
gophers                http                   httpproxy
https                  icecast                ipfs_gateway
ipns_gateway           libamqp                librist
librtmp                librtmpe               librtmps
librtmpt               librtmpte              libsmbclient
libsrt                 libssh                 libzmq
md5                    mmsh                   mmst
pipe                   prompeg                rtmp
rtmpe                  rtmps                  rtmpt
rtmpte                 rtmpts                 rtp
sctp                   srtp                   subfile
tcp                    tee                    tls
udp                    udplite                unix
```

</details>

<details>
<summary><strong>Parsers (68)</strong></summary>

```
aac                    aac_latm               ac3
adx                    ahx                    amr
apv                    av1                    avs2
avs3                   bmp                    cavsvideo
cook                   cri                    dca
dirac                  dnxhd                  dnxuc
dolby_e                dpx                    dvaudio
dvbsub                 dvd_nav                dvdsub
evc                    ffv1                   flac
ftr                    g723_1                 g729
gif                    gsm                    h261
h263                   h264                   hdr
hevc                   ipu                    jpeg2000
jpegxl                 jpegxs                 lcevc
misc4                  mjpeg                  mlp
mpeg4video             mpegaudio              mpegvideo
opus                   png                    pnm
prores                 prores_raw             qoi
rv34                   sbc                    sipr
tak                    vc1                    vorbis
vp3                    vp8                    vp9
vvc                    webp                   xbm
xma                    xwd
```

</details>

<details>
<summary><strong>Bitstream Filters (50)</strong></summary>

```
aac_adtstoasc          ahx_to_mp2             apv_metadata
av1_frame_merge        av1_frame_split        av1_metadata
chomp                  dca_core               dovi_rpu
dts2pts                dump_extradata         dv_error_marker
eac3_core              eia608_to_smpte436m    evc_frame_merge
extract_extradata      filter_units           h264_metadata
h264_mp4toannexb       h264_redundant_pps     hapqa_extract
hevc_metadata          hevc_mp4toannexb       imx_dump_header
lcevc_metadata         media100_to_mjpegb     mjpeg2jpeg
mjpega_dump_header     mov2textsub            mpeg2_metadata
mpeg4_unpack_bframes   noise                  null
opus_metadata          pcm_rechunk            pgs_frame_merge
prores_metadata        remove_extradata       setts
showinfo               smpte436m_to_eia608    text2movsub
trace_headers          truehd_core            vp9_metadata
vp9_raw_reorder        vp9_superframe         vp9_superframe_split
vvc_metadata           vvc_mp4toannexb
```

</details>

<details>
<summary><strong>Hardware Accelerators (77)</strong></summary>

```
av1_d3d11va            av1_d3d11va2           av1_d3d12va
av1_dxva2              av1_nvdec              av1_vaapi
av1_vdpau              av1_videotoolbox       av1_vulkan
dpx_vulkan             ffv1_vulkan            h263_vaapi
h263_videotoolbox      h264_d3d11va           h264_d3d11va2
h264_d3d12va           h264_dxva2             h264_nvdec
h264_vaapi             h264_vdpau             h264_videotoolbox
h264_vulkan            hevc_d3d11va           hevc_d3d11va2
hevc_d3d12va           hevc_dxva2             hevc_nvdec
hevc_vaapi             hevc_vdpau             hevc_videotoolbox
hevc_vulkan            mjpeg_nvdec            mjpeg_vaapi
mpeg1_nvdec            mpeg1_vdpau            mpeg1_videotoolbox
mpeg2_d3d11va          mpeg2_d3d11va2         mpeg2_d3d12va
mpeg2_dxva2            mpeg2_nvdec            mpeg2_vaapi
mpeg2_vdpau            mpeg2_videotoolbox     mpeg4_nvdec
mpeg4_vaapi            mpeg4_vdpau            mpeg4_videotoolbox
prores_raw_vulkan      prores_videotoolbox    prores_vulkan
vc1_d3d11va            vc1_d3d11va2           vc1_d3d12va
vc1_dxva2              vc1_nvdec              vc1_vaapi
vc1_vdpau              vp8_nvdec              vp8_vaapi
vp9_d3d11va            vp9_d3d11va2           vp9_d3d12va
vp9_dxva2              vp9_nvdec              vp9_vaapi
vp9_vdpau              vp9_videotoolbox       vp9_vulkan
vvc_vaapi              wmv3_d3d11va           wmv3_d3d11va2
wmv3_d3d12va           wmv3_dxva2             wmv3_nvdec
wmv3_vaapi             wmv3_vdpau
```

</details>

<details>
<summary><strong>Input Devices (20)</strong></summary>

```
alsa                   android_camera         avfoundation
decklink               dshow                  fbdev
gdigrab                iec61883               jack
kmsgrab                lavfi                  libcdio
libdc1394              openal                 oss
pulse                  sndio                  v4l2
vfwcap                 xcbgrab
```

</details>

<details>
<summary><strong>Output Devices (10)</strong></summary>

```
alsa                   audiotoolbox           caca
decklink               fbdev                  oss
pulse                  sndio                  v4l2
xv
```

</details>
