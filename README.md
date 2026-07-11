# DFU Smart Insole — Public Data Export

Static, public, unauthenticated JSON export of plantar-pressure FSR readings from
the DFU Smart Insole (Arduino Nano 33 BLE). For SEFH / ISEF 2026.

## Endpoints
- `api/export.json` — array of readings (`timestamp`, `calcaneus`, `metatarsal1`, `metatarsal3`, `metatarsal5`, `activity`, `battery_pct`)
- `api/meta.json` — summary (sampling rate, channel map, session count, date range, calibration notes)

## Channel map
| Field | Sensor | Arduino pin |
|-------|--------|-------------|
| calcaneus | Heel | A3 |
| metatarsal1 | Big Toe (1st met) | A2 |
| metatarsal3 | Ball (3rd met) | A1 |
| metatarsal5 | Little Toe (5th met) | A0 |

Values are raw 12-bit ADC counts (0–4095); higher = more pressure.

## Updating the data
The current payload is a synthetic placeholder (`data_source: "synthetic_placeholder"` in
`api/meta.json`). To publish a real capture: export a session from the dashboard
("Export analysis JSON"), replace `api/export.json` (and regenerate `api/meta.json`),
commit, and push. The public URL stays the same.
