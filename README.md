# A&D Balance LabVIEW Instrument Driver

LabVIEW Plug and Play instrument driver for A&D weighing balances.

| | |
|---|---|
| **Driver type** | LabVIEW Plug and Play (non-project style, single LLB) |
| **Source folder** | [`A&D/`](A%26D/) |
| **Manufacturer** | A&D Company |
| **Instrument type** | Electronic balance |
| **Certification** | NI Certified |

## Supported Instruments

- A&D balances with an RS-232 serial interface, including the EK-i/EW-i series.
- Some VIs are series-specific: `A&D EK_EW Zero.vi` works only with the EK-i/EW-i
  series, and `A&D Internal Calibration.vi` needs a balance with an internal calibration
  mass. Check each VI's description before use.

## Supported Interfaces

- Serial (RS-232)

## Driver VIs

| VI | Description |
|---|---|
| `A&D Initialize.vi` | Configures the serial port and opens a session to the balance |
| `A&D Get Weight & Unit.vi` | Reads the current weight value and unit |
| `A&D Get Stable Weight.vi` | Reads the weight once the measurement is stable |
| `A&D Data Separate.vi` | Splits a balance data string into value and unit |
| `A&D Zero.vi` | Re-zeros the display (same as the Re-zero key) |
| `A&D EK_EW Zero.vi` | Re-zero for EK-i/EW-i series balances |
| `A&D Internal Calibration.vi` | Runs internal calibration (balances with an internal mass) |
| `A&D Power OnOff.vi` | Switches the balance display on or off |
| `A&D Close.vi` | Closes the session |
| `A&D Example (Command).vi` | Sends Q (data request) repeatedly and graphs the weight |
| `A&D Example (Print Key).vi` | Graphs data sent when the balance PRINT key is pressed |
| `A&D VI Tree.vi` | Overview of all driver VIs |

## Requirements

- LabVIEW
- [NI-VISA](https://www.ni.com/en/support/downloads/drivers/download.ni-visa.html)
- An RS-232 port (or USB-to-serial adapter) and a cable to the balance

## Repository Layout

```
A&D/
├── A&D.llb             All driver and example VIs
├── dir.mnu             Top-level palette
├── action_status.mnu   Action/Status sub-palette
├── data.mnu            Data sub-palette
├── utility.mnu         Utility sub-palette
└── examples.mnu        Examples sub-palette
```

## Getting Started

1. Install LabVIEW and NI-VISA.
2. Clone this repository, or download it as a ZIP.
3. Copy the [`A&D/`](A%26D/) folder to `<LabVIEW>\instr.lib\` and restart LabVIEW. The
   driver appears on the **Instrument I/O » Instrument Drivers** palette.
4. Connect the balance to a serial port and find its VISA resource name (e.g.
   `ASRL1::INSTR`) in NI MAX. Make sure the balance's baud rate, parity, and data bits
   match the serial settings on `A&D Initialize.vi`.
5. Open `A&D Example (Command).vi` from `A&D.llb`, select the serial port, and run it.

## Known Issues

- None.

## Support

Report driver bugs and feature requests through [GitHub Issues](https://github.com/ASingh-NI/instr-driver-a-and-d-lv/issues).

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md). Do not report security vulnerabilities through public GitHub issues.

## License

See [LICENSE.md](LICENSE.md).
