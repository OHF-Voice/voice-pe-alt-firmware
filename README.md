> [!WARNING]
> This project is experimental and not supported.

# Voice PE alternate firmware

Builds alternative firmware for the [Home Assistant Voice PE](https://github.com/esphome/home-assistant-voice-pe) and publishes an [ESP Web Tools](https://esphome.github.io/esp-web-tools/) install page to GitHub Pages.

**➡️ Install page: https://ohf-voice.github.io/voice-pe-alt-firmware/**

## Available Firmware

| Firmware | Description |
| --- | --- |
| [`voice-pe-streaming-wakeword`](https://ohf-voice.github.io/voice-pe-alt-firmware/voice-pe-streaming-wakeword/) | Adds support for streaming wake word detection in Home Assistant, alongside on-device wake word detection. Based on [PR #599](https://github.com/esphome/home-assistant-voice-pe/pull/599). |

### How the configs are structured

Each buildable `voice-pe-*.yaml` is a small **factory wrapper** (modeled on
upstream's `home-assistant-voice.factory.yaml`): it `!include`s a base config and
adds the improv BLE/serial Wi-Fi provisioning stack. The wrapper is required —
the bare base config has no Wi-Fi SSID/AP and won't build on its own.

The workflow builds every `voice-pe-*.yaml` in the repo root and publishes each at
its own sub-path (e.g. `…/voice-pe-streaming-wakeword/`). To add another build,
add a `voice-pe-<feature>.yaml` wrapper (plus its base config) — no workflow
changes needed.
