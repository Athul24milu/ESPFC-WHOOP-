# ESP FPV / ATHUL L3 - prototype fabrication revision

Updated 11 November 2026. Open ESP_FPV_ATHUL_IOGROUPED.kicad_pro in KiCad 10.

## Current validation
Official KiCad 10.0.3 checks after zone refill: **0 errors, 0 warnings, 0 unconnected items, 0 schematic parity issues and 0 ERC violations**. No PCB DRC checks were disabled and no DRC exclusions were added. ERC uses the unchanged L2 project rules. The former 55 PCB warnings are resolved.

Nine track approaches now terminate at their via centers. Only the short approach sections changed, preserving the surrounding routes. All 75 footprints, their pad geometry, pad nets, mounting holes and the board outline are unchanged from L2. MPU-6050 exposed-die clearance and the five OSD thermal vias are verified. Mask spacing passes the independent check.

## Printed labels
Text uses KiCad stroke lettering, 1.00 mm high with 0.15 mm strokes. Tight connector areas use short codes: B=battery, C=camera video, V=video output, S=SmartAudio, R=FC RX, T=FC TX. Polarity marks are compact graphic symbols with 0.15 mm strokes beside the original pads. Decorative separator lines were moved to the non-fabricated drawing layer. The logo remains. See the updated L3 guides and actual exported top/bottom images.

## Order settings
Upload only ESP_FC_L3_PCB_ONLY_GERBERS.zip. Four layers, 40 x 40 mm nominal outline, 1.00 mm FR4, 35 um / 1 oz copper on ALL FOUR layers, white mask, black legend and ENIG. Standard through vias, minimum drill 0.20 mm. There are 113 plated via holes and four 2.10 mm NPTH mounting holes. The ZIP has 11 Gerbers, two drills and order notes; no BOM or component data.

## Assembly and use
L2 component values and firmware assignments remain valid in L3. SDA GPIO5, SCL GPIO43 and PWM3 GPIO39; explicitly configure I2C because GPIO6 is PWM4. Fit C17=220pF C0G and C20=2.2nF X7R 50V. Use insulating M2 hardware. The L2-named purchase BOM applies unchanged to the L3 component set; sourcing candidates still need the confirmations marked in the BOM.

Bare-board fabrication checks do not establish flight readiness. First power with current limiting, then validate supply behavior, IMU, video and motor outputs on the assembled prototype. Confirm the fabricator's order proof before production.
