{% assign device = site.data.devices[page.device] %}

{%- if device.before_install %}
{% capture path %}templates/device_specific/{{ device.before_install }}.md{% endcapture %}
{% include {{ path }} %}
{%- endif %}

## Basic requirements

{% include alerts/important.html content="Please read through the instructions at least once before actually following them, so as to avoid any problems due to any missed steps!" %}

1. Make sure your computer has `adb`{% unless device.install_method == 'heimdall' or device.install_method == 'dd' %} and `fastboot`{% endunless %}. Setup instructions can be found [here]({{ "adb_fastboot_guide.html" | relative_url }}).
2. Enable [USB debugging]({{ "adb_fastboot_guide.html#setting-up-adb" | relative_url }}) on your device.

{% if device.required_bootloader %}
## Special requirements

{%- capture bootloader %}
Your device must be on bootloader version {% for el in device.required_bootloader %} {% if forloop.last %} `{{ el }}` {% else %} `{{ el }}` / {% endif %} {% endfor %}, otherwise the instructions found in this page will not work.
The current bootloader version can be checked by running the command `getprop ro.bootloader` in a terminal app or an `adb shell` from a command prompt (on Windows) or terminal (on Linux or macOS) window.
{% endcapture %}
{% include alerts/warning.html content=bootloader %}
{%- endif %}

{%- if device.install_method %}
{% capture recovery_install_method %}templates/recovery_install_{{ device.install_method }}.md{% endcapture %}
{% include {{ recovery_install_method }} %}
{%- else %}
## Unlocking the bootloader / Installing a custom recovery

There are no recovery installation instructions for this discontinued device.
{%- endif %}

{%- if device.before_conquer_install %}
{% capture path %}templates/device_specific/{{ device.before_conquer_install }}.md{% endcapture %}
{% include {{ path }} %}
{%- endif %}

## Installing ConquerOS from recovery

{%- capture userspace_architecture -%}
{%- if device.architecture.userspace -%}
{{ device.architecture.userspace }}
{%- else -%}
{{ device.architecture }}
{%- endif -%}
{%- endcapture -%}

1. Download the [ConquerOS installation package](https://download.conqueros.co/{{ device.codename }}) that you would like to install or [build]({{ "devices/" | append: device.codename | append: "/build" | relative_url }}) the package yourself.
2. If you are not in recovery, reboot into recovery:
    * {{ device.recovery_boot }}
{%- if device.uses_twrp %}
3. Now tap **Wipe**.
4. Now tap **Format Data** and continue with the formatting process. This will remove encryption and delete all files stored in the internal storage.
{%- if device.is_ab_device %}
{%- else %}
5. Return to the previous menu and tap **Advanced Wipe**, then select the *Cache* and *System* partitions and then **Swipe to Wipe**.
{%- endif %}
6. Sideload the ConquerOS `.zip` package:
    * On the device, select "Advanced", "ADB Sideload", then swipe to begin sideload.
    * On the host machine, sideload the package using: `adb sideload filename.zip`.
        {% include alerts/tip.html content="If the process succeeds the output will stop at 47% and report `adb: failed to read command: Success`." %}
{%- else %}
3. Now tap **Factory Reset**, then **Format data / factory reset** and continue with the formatting process. This will remove encryption and delete all files stored in the internal storage, as well as format your cache partition (if you have one).
5. Return to the main menu.
6. Sideload the ConquerOS `.zip` package:
    * On the device, select "Apply Update", then "Apply from ADB" to begin sideload.
    * On the host machine, sideload the package using: `adb sideload filename.zip`.
        {% include alerts/tip.html content="If the process succeeds the output will stop at 47% and report `adb: failed to read command: Success`." %}
{%- endif %}
{%- if device.is_ab_device and device.uses_twrp %}
7. _(Optionally)_: If you want to install any additional add-ons, run `adb reboot sideload`, then `adb sideload filename.zip` those packages in sequence.
{%- elsif device.is_ab_device %}
7. _(Optionally)_: If you want to install any additional add-ons, click `Advanced`, then `Reboot to Recovery`, then when your device reboots, click `Apply Update`, then `Apply from ADB`, then `adb sideload filename.zip` those packages in sequence.
{%- else %}
7. _(Optionally)_: If you want to install any additional add-ons, repeat the sideload steps above for those packages in sequence.
{%- endif %}
{% if device.uses_twrp != true %}
    {% include alerts/note.html content="Additional add-ons aren't signed with ConquerOS's official key, and therefore when they are sideloaded, Recovery  will present a screen that says `Signature verification failed`, this is expected, please click `Continue`." %}
{%- endif %}
    {% include alerts/note.html content="If you want Google Apps on your device, you must follow this step **before** booting into ConquerOS for the first time!" %}
{%- if device.current_branch == 17.1 %}
{%- if device.uses_twrp and device.is_ab_device != true %}
8. Once you have installed everything successfully, run 'adb reboot'.
{%- else %}
8. Once you have installed everything successfully, click the back arrow in the top left of the screen, then "Reboot system now".
{%- endif %}
{%- endif %}

{% include alerts/specific/warning_recovery_app.html %}

## Get assistance

If you have any questions or get stuck on any of the steps, feel free to ask on [our Telegram group](https://t.me/conqueroschat).