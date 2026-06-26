cmake_minimum_required(VERSION 3.22)

project(PA_SAFE VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)
FetchContent_Declare(
    JUCE
    GIT_REPOSITORY https://github.com/juce-framework/JUCE.git
    GIT_TAG 8.0.6
)
FetchContent_MakeAvailable(JUCE)

juce_add_plugin(PA_SAFE
    COMPANY_NAME "PA SAFE"
    BUNDLE_ID "com.pasafe.audio"
    PLUGIN_MANUFACTURER_CODE Psaf
    PLUGIN_CODE Saf1
    FORMATS VST3 AU Standalone
    PRODUCT_NAME "PA SAFE"
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE
    NEEDS_MIDI_OUTPUT FALSE
    IS_MIDI_EFFECT FALSE
    EDITOR_WANTS_KEYBOARD_FOCUS FALSE
    COPY_PLUGIN_AFTER_BUILD TRUE
)

juce_generate_juce_header(PA_SAFE)

target_sources(PA_SAFE
    PRIVATE
        Source/PluginProcessor.cpp
        Source/PluginEditor.cpp
)

target_compile_definitions(PA_SAFE
    PUBLIC
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
        JUCE_VST3_CAN_REPLACE_VST2=0
)

target_link_libraries(PA_SAFE
    PRIVATE
        juce::juce_audio_utils
        juce::juce_dsp
    PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags
)
