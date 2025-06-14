# WalterModem ChangeLog

This is the Changelog for WalterModem

## [V1.1.2](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.1.2)

### features

- Added support for light sleep.

### Bug Fixes

- Changed the `CORE_DEBUG_LEVEL` macro to the `ARDUINO` macro to distinguish between ESP-IDF and Arduino.

## [V1.1.3](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.1.3)

### Features

- Update component file with extra metadata.
- Updated examples to use component registry for ESP-IDF.

### Bug Fixes

- Fixed compile errors for `ESP-IDF V5.4.0`

## [V1.2.0](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.1.2)

### Features

- Reworked MQTT implementation

#### event system

- Added System Event Handlers (Registration, System, AT)
- Added MQTT event handler
- Added HTTP event handler
- Added CoAP event handler
- Added GNSS event handler

#### restructuring

- Separated Socket implementation (proto/WalterSocket.cpp)
- Separated MQTT implementation (proto/WalterMQTT.cpp)
- Separated HTTP implementation (proto/WalterHTTP.cpp)
- Separated GNSS implementation (proto/WalterGNSS.cpp)
- Separated BlueCherry implementation (proto/WalterBlueCherry.cpp)

- Regionised the Code Base for easier navigation. (search by region)

- Separated Common Defines (WalterDefines.h)

#### CONFIG

- added support for [`KCONFIG`](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/kconfig.html) (ESP-IDF)
- added support for disabling unused protocols (ESP-IDF,ARDUINO)
- added CONFIG macro.

#### Breaking changes

1) createPDPContext => definePDPContext
2) authenticatePDPContext => setAuthParams
3) socketCreate => socketConfig
4) configSocket => socketConfigExtended
5) connectSocket => socketDial
6) clock is now a struct which contains the `epochTime` and the `timeZoneOffset`

`all examples have been reworked.`

## [v1.2.1](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.1.2)

### Bug Fixes

- fixed `out of bounds` compile error in release mode ([#46](https://github.com/QuickSpot/walter-esp-idf/issues/46))
- fixed mqttConfig wrong defaults ([#47](https://github.com/QuickSpot/walter-esp-idf/issues/47))
- fixed bug in socketConfig where there was a redundant _pdpContextGet ([#51](https://github.com/QuickSpot/walter-esp-idf/issues/51))
- fixed bug where numbers where not converted correctly in socketListen ([#52](https://github.com/QuickSpot/walter-esp-idf/issues/52))
- fixed bug where the queueProcessingTask could get stuck due to having the same task priority (IDLE) ([#53](https://github.com/QuickSpot/walter-esp-idf/issues/53))
- fixed issue where socketListen did not have the option to pass the protocol ([#54](https://github.com/QuickSpot/walter-esp-idf/issues/54))
- fixed bug where the socketRing handler has the wrong starting offset ([#55](https://github.com/QuickSpot/walter-esp-idf/issues/55))
- fixed bug where numbers where not converted correctly in socketReceive ([#56](https://github.com/QuickSpot/walter-esp-idf/issues/56))
- fixed bug where tlsWriteCredential is private ([#66](https://github.com/QuickSpot/walter-esp-idf/issues/66))

### Docs

- updated documentation for definePDPContext([#50](https://github.com/QuickSpot/walter-esp-idf/issues/50))

## [v1.3.0](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.3.0)

### Features

- completely reworked the parsing logic from scratch to make the parser more streamlined and performant ([#60](https://github.com/QuickSpot/walter-esp-idf/commit/96cf8a11f4b11a48cdcb1ac65b50a8466612b610))


### Bug Fixes

- fixed bug in the positioning example where the modem clock could have been set but not the gnss clock which would cause the example to crash ([#40](https://github.com/QuickSpot/walter-arduino/commit/1186de955351ab41da8b128c8cec31d735bc385d)).
- fixed issues with socketReceive ([#60](https://github.com/QuickSpot/walter-esp-idf/commit/96cf8a11f4b11a48cdcb1ac65b50a8466612b610)).
- fixed httpConfigProfile timeout bug which would cause crashes in some cases ([#20](https://github.com/QuickSpot/walter-esp-idf/commit/d3a7da0e66fbaf555d4ab2940043ca290a0c9177)).
- added delay to BlueCherry example, as it would otherwise continuously poll the server ([#72](https://github.com/QuickSpot/walter-esp-idf/commit/3d0f4e5ca57c1aac28dbc922682d8ec83f39f4f9)).

## [v1.3.1](https://github.com/QuickSpot/walter-esp-idf/releases/tag/v1.3.1)

### Bug Fixes

- fixed bug where tlsWriteCredential is private, `again`