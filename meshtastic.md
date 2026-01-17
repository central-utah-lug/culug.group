---
layout: page
title: meshtastic
permalink: /meshtastic/
---

## Configure Intermountain Mesh (AKA Freq51)

Connect Meshtastic receiver to phone, laptop, etc. via USB or Bluetooth.

### Lora settings

Region: United States

Preset: Medium Range - Fast (a.k.a. Medium Fast)

[x] OK to MQTT

Number of hops: 7

Frequency slot: 51

### User settings

(These settings should be unique but not expose private information like full names)

Short name: lshX (i.e. `lsh3`)

Long name: lsh-[devicetype] (i.e. `lsh-deck`)

### Channel settings

Add the Freq51 channel as the primary channel:

- Channel Name: `Freq51`
- Key size: 1 byte
- Key: `1A==`

### Additional info

https://freq51.net/onboarding

## Add `culug` secondary channel

Name: `culug`

Key size: 128 bit

Key: `uLQL3E2hvTZPQduOkEmfmw==`

[ ] Position enabled

[ ] Precise location
