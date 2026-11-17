<img src="https://raw.githubusercontent.com/barloew/satel-link/main/custom_components/satel_link_companion/brand/icon.png" alt="Satel Link Companion" width="96" align="right">

# Satel Link Companion

[![Release][release-badge]][release-url]
[![HACS][hacs-badge]][hacs-url]
[![Validate][validate-badge]][validate-url]

Virtual zones and a master alarm panel for Satel Integra in Home Assistant.

Extends your existing Satel integration. It uses that integration's connection, so the panel's single network connection stays free.

## Features

- **Virtual zones:** turns any Home Assistant sensor, such as a Zigbee door contact or a Z-Wave smoke detector, into a real Satel zone. Useful with an ETHM-1 module, which has no virtual zones of its own.
- **Arm-aware forwarding:** burglary sensors trip the panel only when their partition is armed, with optional entry and exit delays. Hazard sensors forward at all times.
- **Master alarm panel:** arms and disarms several partitions as one, with separate partition sets for Home, Away and Night. Works with HomeKit.
- **Pre-arm check:** lists every open door or window across all partitions before arming.
- **Events and sensors:** for alarms, blocked arms and failed arms, ready for notifications and automations.
- **Roller shutters:** combines a Satel up/down output pair into one cover.

## Requirements

- Home Assistant 2025.7 or later
- Satel INTEGRA or INTEGRA Plus with an ETHM-1 or ETHM-1 Plus module, with integration enabled
- A working Satel integration: [`satel_integra`](https://www.home-assistant.io/integrations/satel_integra/) (core) or `ha_satel_integra_ext`

## Installation

### HACS

[![Open in HACS][my-ha-badge]][my-ha-url]

Or add it manually:

1. In HACS, open the menu and select **Custom repositories**.
2. Add `https://github.com/barloew/satel-link` with category **Integration**.
3. Download **Satel Link Companion** and restart Home Assistant.

### Manual

Copy `custom_components/satel_link_companion` from the [latest release][release-url] to your `config/custom_components` folder and restart Home Assistant.

## Configuration

Before your first link, check the Satel-side settings in the [DLOADX checklist](docs/advanced.md).

1. Go to **Settings → Devices & services → Add integration** and select **Satel Link Companion**. It detects your Satel integration automatically.
2. Run **Map Satel Integra system structure** once to read the panel layout.
3. From the integration page, add what you need. Each becomes its own device:
   - **Link a sensor:** a Home Assistant sensor as a Satel zone
   - **Roller shutter:** an output pair as one cover
   - **Master panel:** one alarm panel for several partitions

## Documentation

- [Advanced guide](docs/advanced.md): DLOADX checklist, master panel, verifying a link, fail-safe behavior
- [Events](docs/events.md): event payloads and example automations
- [Satel object types](docs/satel-types.md): zone functions, wiring types and output functions

## Safety

This integration controls a real alarm system. It fails safe: if a sensor drops out or Home Assistant restarts, a linked zone returns to rest instead of raising an alarm. Verify the behavior with your own hardware before relying on it.

## License

[MIT](LICENSE). Not affiliated with SATEL sp. z o.o.

[release-badge]: https://img.shields.io/github/v/release/barloew/satel-link
[release-url]: https://github.com/barloew/satel-link/releases
[hacs-badge]: https://img.shields.io/badge/HACS-Custom-41BDF5.svg
[hacs-url]: https://github.com/hacs/integration
[validate-badge]: https://github.com/barloew/satel-link/actions/workflows/validate.yml/badge.svg
[validate-url]: https://github.com/barloew/satel-link/actions/workflows/validate.yml
[my-ha-badge]: https://my.home-assistant.io/badges/hacs_repository.svg
[my-ha-url]: https://my.home-assistant.io/redirect/hacs_repository/?owner=barloew&repository=satel-link&category=integration
