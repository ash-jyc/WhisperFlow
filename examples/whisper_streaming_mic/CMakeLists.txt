if (WHISPER_SDL2)
    find_package(PkgConfig REQUIRED)
    pkg_check_modules(PORTAUDIO REQUIRED portaudio-2.0)
    
    # whisper_streaming_mic
    set(TARGET whisper_streaming_mic)
    add_executable(${TARGET} 
        whisper_streaming_mic.cpp
    )

    include(DefaultTargetOptions)

    target_include_directories(${TARGET} PRIVATE ${PORTAUDIO_INCLUDE_DIRS})

    target_link_libraries(${TARGET} PRIVATE common common-sdl whisper ${CMAKE_THREAD_LIBS_INIT} ${PORTAUDIO_LIBRARIES})

    target_compile_options(${TARGET} PRIVATE ${PORTAUDIO_CFLAGS_OTHER})

endif ()
