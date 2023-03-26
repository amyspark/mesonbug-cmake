project('test', 'c')

cmake = import('cmake')

openALOptions = cmake.subproject_options()
# OpenAL can NOT be built with c++17 -- see almalloc.cpp
openALOptions.set_override_option('cpp_std', 'c++14')
openALOptions.set_override_option('strip', 'false')
# Disable Git because Meson somehow gets confused with the
# custom version generator
openALOptions.add_cmake_defines({
    'CMAKE_BUILD_TYPE': 'RelWithDebInfo',
    'ALSOFT_UTILS': false,
    'ALSOFT_NO_CONFIG_UTIL': true,
    'ALSOFT_EXAMPLES': false,
    'ALSOFT_CONFIG': false,
    'ALSOFT_HRTF_DEFS': false,
    'ALSOFT_AMBDEC_PRESETS': false,
    'ALSOFT_BACKEND_ALSA': false,
    'ALSOFT_BACKEND_OSS': false,
    'ALSOFT_BACKEND_SOLARIS': false,
    'ALSOFT_BACKEND_SNDIO': false,
    'ALSOFT_BACKEND_PORTAUDIO': false,
    'ALSOFT_BACKEND_PULSEAUDIO': false,
    'ALSOFT_BACKEND_COREAUDIO': false,
    'ALSOFT_BACKEND_JACK': false,
    'ALSOFT_BACKEND_OPENSL': false,
    'ALSOFT_BACKEND_WAVE': true,
    'ALSOFT_BACKEND_WINMM': false,
    'ALSOFT_BACKEND_DSOUND': false,
    'ALSOFT_REQUIRE_WASAPI': true,
    'ALSOFT_CPUEXT_NEON': false,
    'CMAKE_DISABLE_FIND_PACKAGE_WindowsSDK': true,
    'CMAKE_DISABLE_FIND_PACKAGE_Git': true,
})

libOpenAL = cmake.subproject('openal-soft', options: openALOptions, required: true).dependency('OpenAL')

exe = executable(
    'main',
    'main.c',
    dependencies: libOpenAL,
    install: true
)
