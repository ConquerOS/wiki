{%- assign device = site.data.devices[page.device] -%}
{% if device.custom_recovery_codename %}
{% assign custom_recovery_codename = device.custom_recovery_codename %}
{% else %}
{% assign custom_recovery_codename = device.codename %}
{% endif %}

## Installing a custom recovery using `edl`

1. Download a custom recovery for your device.
2. Connect your device to your PC via USB.
3. On the computer, open a command prompt (on Windows) or terminal (on Linux or macOS) window, and type:
```
adb reboot edl
```
    {% if device.edl_boot %}
    You can also boot into edl mode via a key combination:

    * {{ device.edl_boot }}
    {% endif %}
4. Flash recovery onto your device by following [this]({{ device.install_recovery_guide }}) guide.
