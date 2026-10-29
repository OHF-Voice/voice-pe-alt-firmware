> [!WARNING]
> This project is experimental and not supported.

# Voice PE alternate firmware

Builds alternative firmware for the [Home Assistant Voice PE](https://github.com/esphome/home-assistant-voice-pe) and publishes an [ESP Web Tools](https://esphome.github.io/esp-web-tools/) install page to GitHub Pages.

**➡️ Install page: https://ohf-voice.github.io/voice-pe-alt-firmware/**

## Available Firmware

| Firmware | Description |
| --- | --- |
| [`voice-pe-streaming-wakeword`](https://ohf-voice.github.io/voice-pe-alt-firmware/voice-pe-streaming-wakeword/) | Adds support for streaming wake word detection in Home Assistant, alongside on-device wake word detection. Based on [PR #599](https://github.com/esphome/home-assistant-voice-pe/pull/599). |
| [`voice-pe-voice-labs`](https://ohf-voice.github.io/voice-pe-alt-firmware/voice-pe-voice-labs/) | A satellite of [Voice Labs](https://github.com/OHF-Voice/voice-labs): wake words detected on the device with models the Voice Labs app pushes, and calls streamed to the app, which recognizes and answers them -- in place of Assist's voice pipeline. Its base config is `voice-labs.yaml`, its component `components/voice_labs`. |

### How the configs are structured

Each buildable `voice-pe-*.yaml` is a small **factory wrapper** (modeled on
upstream's `home-assistant-voice.factory.yaml`): it `!include`s a base config and
adds the improv BLE/serial Wi-Fi provisioning stack. The wrapper is required —
the bare base config has no Wi-Fi SSID/AP and won't build on its own.

The workflow builds every `voice-pe-*.yaml` in the repo root and publishes each at
its own sub-path (e.g. `…/voice-pe-streaming-wakeword/`). To add another build,
add a `voice-pe-<feature>.yaml` wrapper (plus its base config) — no workflow
changes needed.

### Voice Labs from a checkout

`voice-labs-local.yaml` builds the Voice Labs firmware with the Wi-Fi from
`secrets.yaml` (`wifi_ssid`, `wifi_password`) instead of improv, for flashing
satellites in development; each after the first gets a name of its own:

```bash
esphome run voice-labs-local.yaml --device <ip>
esphome -s name voice-labs-vpe-2 -s friendly_name "Voice Labs VPE 2" run voice-labs-local.yaml
```

An early prototype Voice PE has 8 MB of flash, not 16: add `-s flash_size 8MB`.
