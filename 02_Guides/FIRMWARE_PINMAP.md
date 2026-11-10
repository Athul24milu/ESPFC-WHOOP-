# L3 firmware pin map — required changes

The PCB and schematic implement these three changes:

- IMU SDA: XIAO D4 / GPIO5, U1 pad 5. Previously PWM3.
- IMU SCL: XIAO D6 / GPIO43, U1 pad 7. Previously SDA.
- Motor 3 PWM: GPIO39 / MTCK auxiliary contact, U1 pad 20. Previously SCL.

Set SDA=GPIO5 and SCL=GPIO43 explicitly. The XIAO default SCL pin, GPIO6, is still assigned to motor PWM4 in this design; do not initialize I2C on the default pin pair. Other signal assignments are unchanged, including the status LED on GPIO44. Use the explicit GPIO numbers in firmware. Configure GPIO39 as a motor output and initialize it low before enabling the driver. Do not use GPIO39 as an external JTAG clock while it controls the motor.

GPIO43 is UART0 TX by default. Disable or remap software UART0 output when it is used for SCL. ROM boot traffic can appear on that pin before firmware; initialize the I2C bus and probe/configure the MPU6050 after startup. Do not use the old FC pin map or factory demo firmware with powered motors.

No flight firmware is included. Verify the IMU identity/address, I2C transactions, axis mapping and all four PWM outputs during bench bring-up before flight.

Primary references:
- https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/
- https://documentation.espressif.com/esp32-s3_datasheet_en.pdf (GPIO matrix, reset states and UART/JTAG pin functions)

