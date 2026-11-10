# ESP FPV / ATHUL L4 - original silkscreen restored

Updated 11 November 2026. Open ESP_FPV_ATHUL_IOGROUPED.kicad_pro in KiCad 10.

## Change scope
Only the original silkscreen text and markings were restored. All 1,023 original artwork objects match L2 by geometry, text, layer and count. Full CAM, VTX, SA, RX, TX and 1S labels, original polarity symbols, separators and logo are back. The L3 short-label redesign and replacement graphic symbols are removed from the printed artwork.

Every corrected L3 track and via is unchanged. All footprints, pad geometry, pad nets, mounting holes and board outline are unchanged. The nine off-center via approach warnings remain resolved. See SILK_RESTORE.json and GEOMETRY_CHECK.json.

## Current checks
KiCad 10.0.3: 0 electrical DRC errors, 0 unconnected items, 0 schematic parity issues, 0 ERC violations. There are 46 visible original text warnings: 26 text-height and 20 text-thickness warnings. No PCB DRC checks were disabled or excluded. ERC uses the unchanged project rules.

Original artwork includes small text below standard 1mm height / 0.15mm stroke guidance. Have JLCPCB accept the artwork proof; fine labels may print poorly. This tradeoff preserves the appearance explicitly requested by the owner.

## Fabrication
Upload only ESP_FC_L4_PCB_ONLY_GERBERS.zip. Four layers, 40 x 40mm nominal outline, 1mm FR4, 1oz / 35um copper on ALL FOUR layers, white mask, black legend and ENIG. Standard through vias, minimum drill 0.20mm. There are 113 plated via holes and four 2.10mm NPTH mounting holes. The ZIP has 11 Gerbers, two separate drill files and order notes; no component or purchasing data.

## Assembly and firmware
Component values and firmware assignments are unchanged: SDA GPIO5, SCL GPIO43, PWM3 GPIO39; GPIO6 is PWM4. The L2-named purchase BOM applies unchanged. C17 is fitted at 220pF C0G; C20 is 2.2nF X7R 50V. Use insulating M2 hardware. Read the firmware pin map and assembly notes. Bench-test the assembled prototype; layout checks do not establish flight readiness.
