---
layout: page
title: Toward Autonomous Room Reservation
description: IoT-based solution using PIR_motion, M5StickC ESP32-PICO, Arduino, Adafruit WINC1500 WiFi Shield, 4G-Dongle, Raspberry Pi,
img: assets/img/headline/m5stack.png
importance: 1
category: work
related_publications: true
---

### System Diagram

```
         (dhcp)         bridge
           ╱    wifi    ┌───────┐
mobile-phone <~.~.~.~.> │(wlan0)│
                        │    br0│RPi
      4G-Dongle <──────>|(eth1) │╲
           ╲    wired   └───────┘╱
         (dhcp)            192.168.66.1
```

<div class="ratio ratio-16x9" style="border-radius: 12px; overflow: hidden;">
  <iframe
    src="https://www.youtube.com/watch?v=1eArDTtim0I&source_ve_path=MTc4NDI0"
    title="Toward Autonomous Room Reservation demo"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen
  ></iframe>
</div>
