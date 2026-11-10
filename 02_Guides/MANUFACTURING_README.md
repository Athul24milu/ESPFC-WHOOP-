# ESP FPV / ATHUL — L2 prototype fabrication revision

Updated 10 November 2026. Open `ESP_FPV_ATHUL_IOGROUPED.kicad_pro` in KiCad 10. The PCB and hierarchical schematic share the same basename; retain the six child schematics, local symbol/footprint libraries and models.

## Completed layout corrections

R5 moved to a courtyard-clean position while retaining its original 0805 land pattern. The R5/Q1 shared-land exception has been removed. SDA, SCL, PWM3 and a displaced GATE2 trace are rerouted using standard through vias. The original MPU6050 ground return remains connected.

All 75 footprints retain their land patterns. R5 is the only moved footprint. All 1,023 original board-level artwork objects match the supplied reference board. No tracks or vias intersect the MPU6050 exposed-die region. Five GND thermal vias remain within the OSD exposed pad.

## Validation

KiCad 10.0.3, after zone refill: 0 electrical DRC errors, 0 unconnected items, 0 schematic parity issues, 0 footprint errors, and 0 ERC violations. All five previously ignored DRC families are enabled. See `DRC_FINAL.json`, `ERC_FINAL.json`, `GEOMETRY_CHECK.json` and `GERBER_AUDIT.json`.

There are 55 visible warnings: 46 original typography findings (26 height, 20 stroke weight) and 9 track endpoints that land within via copper away from the via centers. No warning was hidden to obtain the electrical result. The source artwork was explicitly retained by request. JLCPCB's published standard legend guidance is 1.0 mm height and 0.15 mm line width; some retained artwork is smaller. Have the fabricator accept the fine artwork/proof before ordering; its fine detail is not guaranteed to print legibly. Source: https://jlcpcb.com/capabilities/pcb-capabilities/

## Files and order requirements

The PCB-only ZIP contains 11 RS-274X Gerber layers, separate plated and nonplated Excellon drills, and PCB order notes. It contains no BOM, placement file, schematic, part list, or component/netlist attributes.

Order four layers, nominal 40 x 40 mm outline, 1.00 mm FR4, 35 um (1 oz) copper on ALL FOUR copper layers, white solder mask, black legend, ENIG, and standard through vias. A default 0.5 oz inner-layer stack is not equivalent. There are 113 plated via holes and four 2.10 mm NPTH mounting holes. Use insulating M2 hardware/isolating washers; masked copper is present under some screw-head projections.

## Assembly and firmware changes

Read `FIRMWARE_PINMAP.md` before using the board. L2 changes SDA to GPIO5, SCL to GPIO43 and PWM3 to GPIO39. The old firmware pin map is incompatible. C17 is now fitted by default at 220 pF C0G; its existing 0805 land pattern is unchanged. See `ASSEMBLY_NOTES.md` for the basis and bring-up requirements.

This is a prototype fabrication revision. Hardware operation, boost load-transient behavior and motor current/temperature limits still require measurement on an assembled board.
