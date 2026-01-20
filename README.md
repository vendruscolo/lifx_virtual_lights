# EOL

This project is no longer being maintained.

I was having connectivity and reliability issues with LIFX controllers, they would drop from the network unexpectedly.
I decided to move on to something else, and I'm now using a ESP32 with WLED flashed, driving the original strips.

# LIFX Virtual Light (for LIFX Z)

This integration shows how you would go ahead and integrate a physical light into Home Assistant.

If you use this integration as a template, make sure you tweak the following places:

 - `manifest.json`: update the requirements to point at your Python library
 - `light.py`: update the code to interact with your library

### Installation

Copy this folder to `<config_dir>/custom_components/example_light/`.

Add the following entry in your `configuration.yaml`:

```yaml
light:
  - platform: lifx_virtual_lights
    name: Name of entity
    target_light: "<serial-of-target-light>"
    zone_start: 0
    zone_end: 31
    turn_on_brightness: 127
    turn_on_duration: 0.3
    turn_off_duration: 0
  - platform: lifx_virtual_lights
    name: Name of entity
    target_light: "<serial-of-target-light>"
    zone_start: 16
    zone_end: 31
    turn_on_brightness: 127
    turn_on_duration: 0.3
    turn_off_duration: 0
```

Some configuration is optional, and has default values:

* `turn_on_brightness`: defaults to 255 (max light);
* `turn_on_duration`: the duration of the transition when turning on the light or changing its color. Defaults to 0.5 seconds;
* `turn_off_duration`: the duration of the transition when turning off the light. Defaults to 0.5 seconds.

I suggest to set the `turn_off_duration` value to 0 (no transition): I noticed that sometimes the light remains on, in a dimmed state when transitions are involved.
