# MULTI_Z_MK_II — Multi-Zone HVAC Controller

ESPHome configuration for **PLC1**, the multi-zone HVAC controller at 1203 Llano.
It runs heating and cooling on both floors: one zone on Floor 1 and four zones on Floor 2.

**Board:** ESP32-S3-DevKitC-1 (esp-idf framework)
**Device name:** `multi-z-mk-ii` (shown in Home Assistant as `MULTI_Z_MK_II`)
**MQTT prefix:** `HVAC_MULTI_Z`

## What it controls

| Area | Details |
|---|---|
| Floor 1 (Zone 0) | Daikin AC1 via Faikin (`Faikout/AC1`), gas furnace relays, selectable heat source: heat pump, gas or combined |
| Floor 2 (Zones 1–4) | Daikin AC2 via Faikin (`Faikout/AC2`), 4 motorised dampers, 2 PWM in-duct fans |
| Thermostats | Hardwired inputs on a PCF8575 for Zones 0, 1, 3 and 4; Zone 2 (bathroom) is an Aqara W100 over Zigbee2MQTT |
| Sensors | BME680 air quality (IAQ 0–500), Zigbee window sensor on Floor 1 |

## Files

| File | Purpose |
|---|---|
| `wip-mk2.yaml` | The ESPHome configuration (work in progress, merged v2) |
| `secrets.yaml.example` | The secret names the config expects, with placeholder values |

## Secrets

The config reads every password and key with `!secret`. Copy `secrets.yaml.example` to
`secrets.yaml` next to the YAML and fill in real values. `secrets.yaml` is listed in
`.gitignore` and must never be committed.

## Related

- [4-Zone HVAC Control](https://casaria.github.io/hvac-zone-control/) — zone spec and homeowner advisory
- [mqtt-hvac-control](https://github.com/casaria/mqtt-hvac-control) — MQTT topics and diagrams
- [ESP32-Faikin](https://casaria.github.io/esp32-faikin/) — the Daikin interface firmware
- [1203 Llano Home Systems](https://casaria.github.io/1203-llano-home-systems/) — index of all project sites
