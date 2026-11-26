# Changelog

## 1.3.1

- Home Assistant discovery messages are now also sent when the app connects to the MQTT broker, not only on the Home Assistant birth message. New entities now appear right after an app update, without restarting Home Assistant or the MQTT broker. Reported in #3.

## 1.3.0

- Circuit B (Diematic 3): new topics `zoneB/targetTemp` (calculated flow temperature, register 32) and `zoneB/departureTemp` (measured flow temperature, register 33), with Home Assistant discovery sensors "Température Calculée Zone B" and "Température Départ Zone B" (°C). Requested in #3.
- New option `mqtt_publish_raw_registers` (default `false`): publishes every register already read by the polling loop as one JSON object on `<topic_prefix>/<client_id>/raw/registers` (retained, only when a value changes). Read-only, raw 16-bit values without unit or scaling (`65535` = `0xFFFF` = not available), no Home Assistant entity created. Empty payload while the regulator is unreachable.

## 1.2.0

- New option `log_level` (`DEBUG`, `INFO`, `WARNING`, `ERROR`; default `INFO`). `DEBUG` logs every ModBus frame sent and received.

## 1.1.0

- Circuit C support (Diematic 3): mode, day/night/anti-frost setpoints, calculated temperature, departure temperature, pump. New option `enable_circuit_c`.
- Automatic reconnection: waits for the ModBus gateway and restarts the bridge every 30 s instead of stopping.
- Default log level set to INFO.

## 1.0.0

- Home Assistant app packaging of [Benoit3/Diematic_to_MQTT](https://github.com/Benoit3/Diematic_to_MQTT): options configured from the UI.
