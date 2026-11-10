# ESPFC WHOOP

ESP FPV / ATHUL - MATRIX40 L4 hardware for a 1S brushed FPV flight-controller project, built around the Seeed XIAO ESP32-S3, MPU-6050 and AT7456E analog OSD.

![Final L4 front and back component views](02_Guides/PCB_TOP_BOTTOM_COMPONENTS_L4.png)

## Start here

- [User manual](02_Guides/ESP_FPV_ATHUL_Brochure_L4.pdf): connections, configuration, installation and troubleshooting.
- [Assembly and component guide](02_Guides/ESP_FPV_ATHUL_Component_Map_L4.pdf): component values, closeups, pin 1, polarity and hidden XIAO contacts.
- [Purchase BOM](03_BOM_and_Purchase/ESP_FC_L2_Purchase_BOM.xlsx): quantities and Robu, Quartz Components and Evelta links. Search-only links and unconfirmed candidates are marked.
- [All-reference BOM CSV](03_BOM_and_Purchase/ESP_FC_L2_BOM_All_75_References.csv): all 75 board references, including 62 fitted component packages and integral PCB features.
- [Package instructions](START_HERE.txt).

## PCB fabrication

Upload only [the PCB-only Gerber ZIP](01_JLCPCB_UPLOAD/ESP_FC_L4_PCB_ONLY_GERBERS.zip) to JLCPCB for bare-board fabrication. It contains 11 Gerber layers, separate plated/nonplated drill files and PCB order notes. It contains no BOM or component purchasing data. Components are assembled at home.

Order four layers, 40 x 40 mm outline, 1.00 mm FR4, ENIG, white solder mask and black legend. Specify 1 oz / 35 um copper on **all four layers**, including the inner layers. Standard through vias are used; the minimum drill is 0.20 mm. Mounting holes are four 2.10 mm NPTH holes. The measured mounting square is 24.65 mm, rotated 45 degrees in the board view; it is not a 25.5 mm pattern.

L4 restores the original silkscreen exactly: all 1,023 artwork objects match the earlier L2 geometry, text, layers and count. Full CAM, VTX, SA, RX, TX and 1S labels, original polarity symbols, separators and logo are restored. **Every corrected L3 track and via remains unchanged.** All footprints, component values, pad nets and mounting dimensions are unchanged; the L2-named purchase BOM still applies.

Current KiCad checks: **0 electrical DRC errors, 0 unconnected items, 0 schematic parity issues and 0 ERC violations**. The original **46 text warnings** are intentionally visible again (26 text-height and 20 text-thickness). The nine via-centering warnings remain resolved. No PCB DRC checks were disabled or excluded; ERC uses the unchanged project rules. Ask JLCPCB to accept the fine original artwork/proof before ordering; small labels may print poorly. Assembled hardware still requires bench validation.

See [manufacturing notes](02_Guides/MANUFACTURING_README.md) and [verification records](05_Verification/).

## Open the design

Open [ESP_FPV_ATHUL_IOGROUPED.kicad_pro](04_KiCad_Project/ESP_FPV_ATHUL_IOGROUPED.kicad_pro) in KiCad 10. Keep the child schematics, local symbol/footprint libraries and models alongside the project. The project is self-contained apart from KiCad's standard installation libraries.

## Firmware and assembly requirements

No ready-to-fly firmware is included. The L4 pin assignments are **IMU SDA GPIO5, IMU SCL GPIO43 and motor 3 PWM GPIO39**. Default XIAO SCL GPIO6 is PWM4 on this PCB. Configure I2C explicitly, manage UART0 TX output on GPIO43, and initialize motor outputs low before motor power.

Read [the firmware pin map](02_Guides/FIRMWARE_PINMAP.md) and [assembly notes](02_Guides/ASSEMBLY_NOTES.md). C17 is fitted at 220 pF C0G; C20 is 2.2 nF X7R 50 V. The MPU-6050 is a bare QFN-24, not a breakout module. First power should use a current-limited supply with motors disconnected. Remove propellers for output checks.

## Package contents

| Folder | Contents |
| --- | --- |
| `01_JLCPCB_UPLOAD` | PCB-only fabrication ZIP |
| `02_Guides` | User manual, assembly guide, PCB views and engineering notes |
| `03_BOM_and_Purchase` | Purchase workbook and all-reference CSV |
| `04_KiCad_Project` | Current editable PCB, schematic, libraries and models |
| `05_Verification` | KiCad, geometry, mask, via and Gerber checks |

`FILE_MANIFEST_SHA256.json` records checksums for the release package. The PCB images are CAD renders, not photographs. Older layout trials are not included.
