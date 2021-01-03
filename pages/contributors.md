---
sidebar: home_sidebar
title: ConquerOS contributors
permalink: contributors.html
versions: [17.1, 16.0]
---

{% assign devices = "" | split: " " %}
{% for device in site.data.devices %}
{% assign devices = devices | push: device[1] %}
{% endfor %}
{% assign sorted = devices | sort: 'name' | sort: 'vendor' %}


## Core Developer
| Name | Username |
|:----:|:--------:|
| Alif Fathur | herobuxx |
| Pulkit Agarwal | Pulkit077 |
{: .table }

## Device Maintainer
| Name | Username |
|:----:|:--------:|
| Alif Fathur | herobuxx |
| Pulkit Agarwal | Pulkit077 |
| Murad | LinuxAlien |
| Hanif Ardhani | HanifArdhani |
| Dheeresh A. | Daredevil07 |
| Sakhtivel Nadar | CosmoFrwak001 |
| Lovepreet Singh | z3nitsu |
{: .table }