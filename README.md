# PA SAFE

PA SAFE is a dedicated stereo safety plugin for PA systems and bass-heavy playback. When enabled, it forces everything below 100 Hz into true mono by replacing the left and right low-frequency content with the same signal on both channels. That makes the sub band stereo correlation `+1.0`.

The plugin also includes a gain knob with a `-10 dB` to `+10 dB` range.

## Controls

- `MONO < 100 Hz`: turns the sub-100 Hz mono safety processing on or off.
- `GAIN`: raises or lowers the output level from `-10 dB` to `+10 dB`.

## Interface

The layout is a gray rectangular plugin faceplate with two center controls: a green mono button and a green gain knob. Large black, slightly oval speaker drums sit on both sides of the controls.

## Audio Behavior

For stereo input, PA SAFE:

1. Low-passes the left and right channels at 100 Hz.
2. Averages that low-frequency content into one mono low band.
3. Replaces both left and right low bands with that identical mono signal.
4. Keeps the higher-frequency stereo content intact.
5. Applies the output gain.

The low band is identical in the left and right outputs whenever the mono button is enabled.

## Build

This project uses CMake and JUCE.

```bash
cmake -S . -B build
cmake --build build --config Release
```

The CMake project fetches JUCE automatically from GitHub. It builds VST3, AU, and Standalone targets.

## Repository Structure

```text
PA-SAFE/
  CMakeLists.txt
  Source/
    PluginProcessor.h
    PluginProcessor.cpp
    PluginEditor.h
    PluginEditor.cpp
```

## Notes

This is source code for a JUCE audio plugin, ready to place in a GitHub repository. To publish it, create a new GitHub repo and add these files.
