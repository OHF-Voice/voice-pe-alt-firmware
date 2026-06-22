# Voice PE alternate firmware (streaming wake word PR build)

Builds alternative firmware for the [Home Assistant Voice PE](https://github.com/esphome/home-assistant-voice-pe) and publishes an [ESP Web Tools](https://esphome.github.io/esp-web-tools/) install page to GitHub Pages.

**➡️ Install page: https://ohf-voice.github.io/voice-pe-alt-firmware/**

## Available Firmware

| Firmware | Description |
| --- | --- |
| [`voice-pe-streaming-wakeword`](https://ohf-voice.github.io/voice-pe-alt-firmware/voice-pe-streaming-wakeword/) | Adds support for streaming wake word detection in Home Assistant, alongside on-device wake word detection. Based on [PR #599](https://github.com/esphome/home-assistant-voice-pe/pull/599). |

### Adding more alternative firmwares

The workflow builds every `voice-pe-*.yaml` in the repo root and publishes each at
its own sub-path (e.g. `…/voice-pe-streaming-wakeword/`). To add another build,
drop a new `voice-pe-<feature>.yaml` in the root — no workflow changes needed.
