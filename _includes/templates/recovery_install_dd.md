{%- assign device = site.data.devices[page.device] -%}
{% if device.custom_recovery_codename %}
{% assign custom_recovery_codename = device.custom_recovery_codename %}
{% else %}
{% assign custom_recovery_codename = device.codename %}
{% endif %}

## Installing a custom recovery using `dd`

1. Download a custom recovery for your device
2. Place the recovery image file on the root of `/sdcard`:
   * Using adb: `adb push <recovery_filename>.img /sdcard/<recovery_filename>.img`
    {% include alerts/tip.html content="The file may not be named identically to what stands in this command, so adjust accordingly." %}
   * You can use any method you are comfortable with. `adb` is universal across all devices, and works both in Android and recovery mode, providing USB debugging is enabled.
3. Now, open an `adb shell` from a command prompt (on Windows) or terminal (on Linux or macOS) window. In that shell, type the following commands:
```
su
dd if=/sdcard/<recovery_filename>.img of={{ device.recovery_partition }}
```
4. Reboot into recovery.
    * From the same shell, type the following command:
```
reboot recovery
```