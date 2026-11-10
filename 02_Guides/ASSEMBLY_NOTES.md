# L3 assembly notes

Retain the specified 0805 parts and the bare MPU6050 QFN-24. No central solder/paste land is provided for the MPU6050 exposed die. The SDA escape uses a conventional 0.20 mm through via outside the QFN land; it joins the larger front-side XIAO contact. Back-side tenting is inherited from the project. Check solder coverage on the large XIAO contact during hand assembly; this is not an HDI/blind-via process.

Fit C17 = 220 pF C0G by default; its previous DNP flag and value annotation have been corrected in both PCB and schematic. It is connected across the 732 kohm upper feedback resistor. With C15 + C16 = 44 uF nominal, the TI recommended 1 kHz feed-forward zero gives 217.4 pF; 220 pF is the selected standard value. Effective ceramic capacitance under bias and load-transient behavior must be checked on the prototype. This choice does not prove loop stability. Reference: TI TPS61023 datasheet, section 8.2.2.4, equation 10: https://www.ti.com/lit/ds/symlink/tps61023.pdf

Use insulating M2 fasteners or insulating washers/grommets. The NPTH holes are clear, but the design does not provide copper-free areas for bare metal screw-head projections.

Program the L3 pin map before motor-power bring-up. Verify supply rails, IMU communication and PWM outputs on the assembled prototype. The unmeasured motor pulse rating and flight performance are not certified by PCB DRC.
